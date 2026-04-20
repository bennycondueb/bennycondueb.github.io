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
After some reasoning, the overall flowchart for the node looked like this: --insert image--  \\
The reasons for choosing Python over C++ for the development of the node were: 
- Time constraint for the Node to be ready. 
- Lack of VO projects in C++ that could be used as reference points.
- Easier test creation and validation. 

## Step 2: Development 
I'd say that this is the fun part for the developer, but not for anyone else who needs to endure it. \\
Mostly because it's boring: write code -> test code -> repeat . And continue this iteration up until you have what were searching for. \\