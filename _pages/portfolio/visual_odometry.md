---

title: Visual Odometry
subtitle: from now on, also "VO" 
permalink: /_pages/portfolio/visual-odometry/
layout: single
author_profile: true
toc: true 
toc_sticky: true

---

# Why? 

The reason "why" behind this project that I was assigned was the following: adding a new source of yaw estimation to our EKF to improve its performance, 
considering that our IMU was subject to heavy drifting. 

# Step 1: Research 

Before writing any line of code, a question needed to be answered: what is Visual Odometry? \\
I was working on path planning and path tracking beforehand, and had no single clue of Visual Odometry was. \\
So I started doing some research. Google, theses, and so on. \\
And I came across [this thesis from Nour Saeed on VO](https://webthesis.biblio.polito.it/12500/1/tesi.pdf) that became my reference point for the algorithm structure of the project. 
I also came across [this repo from @SharanIO](https://github.com/SharanIO/Visual-Odometry/blob/main/src/svo.py) that became useful for understanding more deeply OpenCV's functions and how a general VO could be implemented in Python. \\
It's important to mention the fact that several state-of-the-art repositories and solutions, such as [ORB-SLAM 3](https://github.com/UZ-SLAMLab/ORB_SLAM3), were 
considered, but discarded due to dependencies conflicts with our pipeline. \\
After some reasoning, the overall flowchart for the node looked like this: ![flowchart for the visual odometry node](/assets/images/vo_pipeline.png){: .align-center}  \\
The reasons for choosing Python over C++ for the development of the node were: 
- Time constraint for the Node to be ready. 
- Lack of VO projects in C++ that could be used as reference points.
- Easier test creation and validation. 
Let's discuss the environment where this VO needed to be applied. \\
Our Pipeline relied upon 2 independent cameras from [Allied Vision]() (NDR: I'm not endorsed nor sponsored by them) mounted below the LiDAR for estimating the cones color. \\
These 2 cameras weren't stereo, nor the team was planning to change to stereo cameras, nor to switch to a single cameras, 
which would've given different constraints during the development. 

# Step 2: Development 
I'd say that this is the fun part for the developer, but not for anyone else who needs to endure it. \\
Mostly because it's boring: write code -> test code -> repeat . And continue this iteration up until you have what were searching for. \\
Consider the image given in Step 1 for the algorithm flowchart and let's dive into the "Extract Left and Right Rotation Matrices". \\

## Extracting features

![Flowchart for the extract left and right rotation matrices component of the visual odometry node](/assets/images/vo_matrix_extraction.png){: .align-center}
First thing first, let's clarify that we are always working with the **2 last images retrieved**. \\
Then, our first objective is to extract the features from each image, this happens thanks to OpenCV's functions: 
``` 
def detect_features(self, img):
    """
    Detect ORB features in the given image and returns the points and the descriptor.
    """
    orb = cv2.ORB_create()
    kp, des = orb.detectAndCompute(img, None)
    kp = cv2.KeyPoint_convert(kp)
    return kp, des
``` 

After we return the descriptors for both images, we double check they are valid, and if they are, we slice them to have matching length: 
``` 
points_first, dsc1 = self.detect_features(first_img)
points_second, dsc2 = self.detect_features(second_img)

# If no descriptors are found, we exit early to avoid matcher errors
if dsc1 is None or dsc2 is None:
    return None

# Simple slicing to prevent problems with mismatching lengths
best_len = min(len(points_first), len(points_second))
points_first = points_first[:best_len]
points_second = points_second[:best_len]
```

## Homography matrix

We double check that we have enough points (for accuracy purposes) and then we compute features and the homography matrix 

```
features_first, features_second = self.track_features(points_first, points_second, dsc1, dsc2)
homo, mask = cv2.findHomography(features_first, features_second, cv2.RANSAC, 5.0)
```

Then, we either decompose the homography matrix or find the essential matrix to obtain the yaw: 

```
# we use homography 
if inlier_ratio < 0.5 or len(features_first) < 40: 
    num, R, t, p = cv2.decomposeHomographyMat(homo, self.camera_intrinsic)
    # score homography using matched points 
    scores = [ self.score_homography_decomposition(
                    R[i], t[i], p[i], self.camera_intrinsic,
                    features_first, features_second
                ) for i in range(num)]
    best_idx = scores.index(max(scores))
    R, t, p = R[best_idx], t[best_idx], p[best_idx]
        
# we use essential 
else:
    E, mask = cv2.findEssentialMat(features_first, features_second, self.camera_intrinsic, cv2.RANSAC)
    if E is None or mask is None:
        return None
    # use matched points
    _, R, t, _ = cv2.recoverPose(E, features_first, features_second, self.camera_intrinsic)

# Basic validity checks on rotation matrix 
if R is None or not np.isfinite(R).all():
    return None
detR = np.linalg.det(R)
if not np.isfinite(detR) or abs(detR - 1.0) > 1e-2:
    return None
        
return R
```

## Yaw Estimation

From this point on, it's trivial the necessity to check the integrity of the rotation matrices, as there are multiple possible points of failure. \\
Let's briefly recall the overall algorithm flowchart before moving on, to better remember what we are trying to achieve: ![flowchart for the visual odometry node](/assets/images/vo_pipeline.png){: .align-center}  \\
Gained the 2 different rotation matrices, the idea is to average their movement together: recall  that the 2 cameras are independent from each other. 
Reason for this is to get a better estimate for the real yaw, considering 2 measurements together instead of a single one. \\
This average is computed through some Linear Algebra, using quaternions: 

```
def averaging_rotation_matrices(self, rot_matrices): 
    # transforming from matrices to quaternions
    quats = np.array([Rotation.from_matrix(Ri).as_quat() for Ri in rot_matrices])  # [x, y, z, w]

    # Ensure consistent quaternion signs (avoids canceling)
    for i in range(1, len(quats)):
        if np.dot(quats[0], quats[i]) < 0:
            quats[i] = -quats[i]

    # Build the symmetric accumulator matrix
    A = np.zeros((4, 4))
    for q in quats:
        q = q.reshape(4, 1)
        A += q @ q.T
        
    # Eigen decomposition
    eigenvalues, eigenvectors = np.linalg.eigh(A)
    q_avg = eigenvectors[:, np.argmax(eigenvalues)]  # principal eigenvector

    # Convert back to rotation matrix
    R_avg = Rotation.from_quat(q_avg).as_matrix()

    return R_avg
```

And now, with a rotation matrix in our hand, extracting the yaw is simply a matter of an arctangent: 

```
R = self.averaging_rotation_matrices([R1, R2])
yaw_vo = np.arctan2(R[1, 0], R[0, 0])
```

## IMU correction

If needed, we can correct this yaw given IMU measurements, so technically and theoretically, this becomes a Visual Inertial Odometry.
As these components are not mandatory for the overall performance, we can close an eye on the technical name :D \\
Nevertheless, here's the code for such IMU correction: 

```
# assuming we have available the IMU yaw and Ground Truth yaw
if isinstance(self.yaw, (int, float)) and isinstance(self.ground_truth_yaw, (int, float)):
    yaw_imu = self.yaw
    yaw_gt = self.ground_truth_yaw
                        
    # update bias estimate (IMU vs GT)
    err_imu_gt = self.normalize_angle(yaw_imu - yaw_gt)
    self._yaw_bias_samples.append(err_imu_gt)
    
    # if we have enough bias samples 
    if len(self._yaw_bias_samples) >= 50:
        self._yaw_bias_estimate = float(np.median(np.array(self._yaw_bias_samples)))
                        
        # apply bias correction 
        yaw_vo_c = self.normalize_angle(yaw_vo - self._yaw_bias_estimate)
        yaw_imu_c = self.normalize_angle(yaw_imu - self._yaw_bias_estimate)
        yaw_gt_c = self.normalize_angle(yaw_gt)

        # feed live plot with corrected and raw values
        self._append_yaw_sample(yaw_vo, yaw_imu_c, yaw_gt_c)
    else:
        self._append_yaw_sample(yaw_vo, None, None)
```

# Step 3: Results

Did the VO Node work? The answer is... kinda. \\
The performance of VO heavily depends on the FPS of the cameras, considering that  _more frames = less differences between images = features align better = less error propagation = better overall result_. \\
This goes against the 10fps our cameras were doing. The reason for our cameras doing **only** 10fps lies upon the fact that they are synchronized with the LiDAR scan, which had a frequency of 10Hz. \\ 
With pre-recorded rosbags, we could see that the VO was approximating the yaw, but now with the precision required for blending it into our EKF. \\
We also faced a problem when the cameras were already in movement and the VO node didn't start yet: the yaw zero would be skewed w.r.t. the actual yaw zero, making the SLAM of the pipeline fail. \\

# Step 4: Conclusions

Even though the Node didn't reach the expected performances, the theory about Visual Odometry was deeply understood and the causes for the poor performance were easily pinpointed. \\
Considering that we didn't want to mess with the cameras driver for the image gathering, we decided to keep the node as a skeleton for a future project. \\
This future project would be using **only** the cameras to dictate our car's pipeline, and this VO would be a good starting point for such future work. \\