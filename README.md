# A-LOAM for kitti dataset

This repository contains modified code of A-LOAM to run and evaluate with kitti-data set. When you run the code, you'll get the trajectory results of A-LOAM in KITTI groundtruth format and you can directly evalutate the result with KITTI gt by EVO-eval kit. A-LOAM already has the kitti helper for kitti-data usage but I found that it has different directories so I also modified it. Wish you find it helpful, especially who are not familiar with ROS and LOAM.

## 1. Prerequisites
### 1.1 **Ubuntu** and **ROS**
Ubuntu 64-bit 16.04 or 18.04.
ROS Kinetic or Melodic. [ROS Installation](http://wiki.ros.org/ROS/Installation)


### 1.2. **Ceres Solver**
Follow [Ceres Installation](http://ceres-solver.org/installation.html).

### 1.3. **PCL**
Follow [PCL Installation](http://www.pointclouds.org/downloads/linux.html).


## 2. Build A-LOAM
Clone the repository and catkin_make:

```
    cd ~/catkin_ws/src
    git clone https://github.com/HKUST-Aerial-Robotics/A-LOAM.git
    cd ../
    rosdep install --from-paths src --ignore-src -r -y
    catkin_make
    source ~/catkin_ws/devel/setup.bash
```

## 3 Making new bagfile from kitti dataset
Download odometry dataset(color or gray, velodyne, calibration, ground truth)
from : http://www.cvlibs.net/datasets/kitti/eval_odometry.php and Merge them all in one dataset directory

### 3.1 Edit the launch file
```
gedit ~/catkin_ws/src/A-LOAM/launch/kitti_helper.launch
```
Change 'dataset_folder' and 'output_bag_file' to your own directories

### 3.2 Run the launch file:
```
roslaunch kittibag kittibag.launch
```
## 4. Run the package

### 4.1 change the result directory in launch file :
```
gedit ~/catkin_ws/src/A-LOAM/launch/aloam_velodyne_HDL_64.launch
```
Change 'RESULT_PATH' to your result dir

### 4.2 Run the launch file:
```
roslaunch aloam_velodyne aloam_velodyne_HDL_64.launch
```

### 4.3 Play existing bag files:
```
rosbag play *.bag --clock 

```
## 5. Evaluation with evo kit
Check and follow this repository
```
https://github.com/MichaelGrupp/evo
```
## 6. Evaluation results
<img src = "https://raw.githubusercontent.com/Mitchell-Lee-93/kitti-A-LOAM/master/A-LOAM/pic/1.png" width = "300"> <img src = "https://raw.githubusercontent.com/Mitchell-Lee-93/kitti-A-LOAM/master/A-LOAM/pic/2.png" width = "300">  <img src = "https://raw.githubusercontent.com/Mitchell-Lee-93/kitti-A-LOAM/master/A-LOAM/pic/3.png" width = "300">

## Original code from
https://github.com/HKUST-Aerial-Robotics/A-LOAM
