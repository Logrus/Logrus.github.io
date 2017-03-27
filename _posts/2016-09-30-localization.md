---
layout: post
title: Master project&#58; Localization with Deep Learning
---

<img src="https://github.com/Dtananaev/localization/raw/master/pictures/correction_net.JPG" class="teaser-img" />
Robot localization with deep neural networks on 2D occupancy grid maps. The goal of the research project is to explore the capabilities of the neural networks to localize the robot on a 2D plane, given the odometry and 2D laser scans.

[The full report can be found here.](https://drive.google.com/open?id=0B0jDQTJWpzD3ZnBHMDY1d0twU3c)

**Authors:** Denis Tananaev, Vladislav Tananaev, Oksana Kutkina

**Source:** [Dtananaev/localization](https://github.com/Dtananaev/localization)

Source contains the following targets:

* simulator - simulates the robot  noisy odometry, front and back 2D laser scans. It also outputs the true pose of the robot. 
The simulator can be used in order to generate the dataset for training of a neural network. Click on the image to see a video demonstration:
[![simulator](https://github.com/Dtananaev/localization/raw/master/pictures/simulator.JPG)](https://www.youtube.com/watch?v=XgUfoiTanBc)
     * To run: 
        * roslaunch simulator simulator.launch - run simulator.
        * roslaunch simulator mbDWA.launch - run move_base- robot motion library. In order to move the robot use the button "2D nav goal"
        
* Scan_matcher - the neural network which uses only 2D laser scans in order to get the x,y,theta triplet representing the pose of a robot. 
In the video below the green is the robot's ground truth pose and red is the position predicted by the network. Click on the image to see a video demonstration: 
[![Scan_matcher](https://github.com/Dtananaev/localization/raw/master/pictures/scan.JPG)](https://www.youtube.com/watch?v=LuZNLaJ75xs)
     * To run: 
         * cd scan_matcher/scripts/
         * python scan_mather.py - this command runs the network online in a simulator.
         * python scan_matcher_train.py - this command runs the network in an online training mode. The network accumulates the data for 10 seconds than makes one epoch of training and updates the weights on the fly. 
         
* recording tools - the tools for recording the simulated odometry, laser scans, true pose from the simulator to txt files. It also contains the tools for visualization of the recorded data.         
* correction_net - the correction network is a network which is based on the idea that if we have a perfect odometry we have solved the localization problem. Since we cannot have the ideal odometry we can learn the noise distribution. So the idea of the correction network is to correct the error produced by the odometry through the use of the laser scan information. This is similar to the standard Kalman filter approach (for the details see [the full report](https://drive.google.com/open?id=0B0jDQTJWpzD3ZnBHMDY1d0twU3c)). 

The correction net architecture is based on the modified version of the VGG network implemented so far only for processing recorded data files in offline settings. The scripts for training and testing are provided. In the video below the green contour is the ground truth, the red contour is the corrected position from the network, and the blue contour is the odometry position.
[![correction_net](https://github.com/Dtananaev/localization/raw/master/pictures/correction_net.JPG)](https://youtu.be/ULN8vkq5_bk)

* Another interesting application of the neural network is to represent the whole map inside the neural network's weights. So in the video below it is possible to see how a simple 4 layers fully connected network could output 181-dimensional vector of distance measurements given only x,y,theta as input.
[![regenerate_map](https://github.com/Dtananaev/localization/raw/master/pictures/laserGen.JPG)](https://www.youtube.com/watch?v=DWMxrn6dcgA)

