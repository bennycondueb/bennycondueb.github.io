---

title: Visual Odometry
subtitle: from now on, also "VO" 
permalink: /_pages/portfolio/visual-odometry/
layout: single
author_profile: true

---

## Why? 
The reason "why" behind this project that I was assigned was the following: adding a new source of yaw estimation to our EKF to improve its performance, 
considering that our IMU was subject to heavy drifting. 

## Step 1: Research 
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

## Step 2: Development 
I'd say that this is the fun part for the developer, but not for anyone else who needs to endure it. \\
Mostly because it's boring: write code -> test code -> repeat . And continue this iteration up until you have what were searching for. \\
Consider the image given in Step 1 for the algorithm flowchart and let's dive into the "Extract Left and Right Rotation Matrices". \\
![Flowchart for the extract left and right rotation matrices component of the visual odometry node](/assets/images/vo_matrix_extraction.png){: .align-center}

## Step 3: Results
Did the VO Node work? The answer is... kinda. \\
The performance of VO heavily depends on the FPS of the cameras, considering that  _more frames = less differences between images = features align better = better overall result_. \\
This goes against the 10fps our cameras were doing. The reason for our cameras doing **only** 10fps lies upon the fact that they are synchronized with the LiDAR scan, which had a frequency of 10Hz. \\ 
With pre-recorded rosbags, we could see that the VO was approximating the yaw, but now with the precision required for blending it into our EKF. \\
We also faced a problem when the cameras were already in movement and the VO node didn't start yet: the yaw zero would be skewed w.r.t. the actual yaw zero, making the SLAM of the pipeline fail. \\

## Step 4: Conclusions
Even though the Node didn't reach the expected performances, the theory about Visual Odometry was deeply understood and the causes for the poor performance were easily pinpointed. \\
Considering that we didn't want to mess with the cameras driver for the image gathering, we decided to keep the node as a skeleton for a future project. \\
This future project would be using **only** the cameras to dictate our car's pipeline, and this VO would be a good starting point for such future work. \\