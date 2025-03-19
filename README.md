# Edge-and-Corner-Detection-in-Unorganized-Point-Clouds

## Overview

This repository contains implementation for a novel edge and corner detection algorithm for unorganized point clouds. The approach enables robust 6D pose estimation of objects in cluttered environments and has been tested for robotic pick and place applications.

## Features

* Fast edge extraction from unorganized 3D point clouds
* Line segment detection and corner point identification
* 6D pose estimation of objects with known dimensions
* Handles raw and noisy data with minimal parameter tuning
* Works in cluttered environments with multiple instances of the same object

## Algorithm Pipeline

1. **Edge Points Extraction** : Classifies points as edge points based on local neighborhood distribution
2. **Line Equation Estimation** : Uses RANSAC to find line equations from edge points
3. **Edge Length Estimation** : Finds extremities of edges to calculate lengths
4. **Corner Detection** : Identifies intersections between edges
5. **Pose Estimation** : Calculates 6D pose using correspondences between detected corners and object model

## Requirements

* PCL (Point Cloud Library)
* ROS (Robot Operating System)
* RGB-D sensor (e.g., Microsoft Kinect)
* 6-DOF robot manipulator (tested with UR5)

## Usage

The system consists of two main modules:

1. **Perception Module** : Processes point cloud data and estimates object poses
2. **Motion Control Module** : Controls robot movement for pick and place operations

### Parameters

* `rs`: Radius for neighborhood search (recommended: 0.02m)
* `th`: Threshold value for edge classification (recommended: 0.35)

## Experimental Results

The algorithm has been tested on:

* Standard 3D objects (coffee mugs, bowls, bunnies, dragons)
* Warehouse scenarios with cartons/bricks
* Both isolated objects and dense clutter

Computation times:

* Edge extraction: ~2.1s
* Line detection: ~2.1-5.3s
* Model fitting: ~0.1-0.2s
* Total: ~4.4-7.6s

## Advantages

* Doesn't require surface reconstruction
* No need for extensive training data
* Works with textureless objects
* Easily adaptable to objects of different dimensions
* Outperforms covariance matrix-based methods on noisy real-world data

## Citation

```
@article{vohra2021edge,
  title={Edge and Corner Detection in Unorganized Point Clouds for Robotic Pick and Place Applications},
  author={Vohra, Mohit and Prakash, Ravi and Behera, Laxmidhar},
  journal={arXiv preprint arXiv:2104.09099},
  year={2021}
}
```

## Authors

* Mohit Vohra, Department of Electrical Engineering, IIT Kanpur, India
* Ravi Prakash, Department of Electrical Engineering, IIT Kanpur, India
* Laxmidhar Behera, Department of Electrical Engineering, IIT Kanpur, India and TCS Innovation Labs, Noida, India
