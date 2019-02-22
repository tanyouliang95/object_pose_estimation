# object_pose_estimation
Simple ROS 2D pointcloud target object pose estimator. Line-based target identifier with user input parameters.

![alt text](/resources/rviz_example.png?)

*Developing!!!!!!!!!!!!!*

## Getting Started

```
cd catkin_ws
catkin_make --pkg object_pose_estimation
source devel/setup.bash
```


**Use ROS Hokoyu Driver Package [here](https://github.com/ros-drivers/urg_node).**
```
roslaunch urg_node urg_lidar.launch ip_address:=XXXXXXX
```

**Conversion from laserscan to pointcloud**
``` 
rosrun object_pose_estimation scan2pcd.cpp 
```

**Main Pose Estimation ROS2 Node**
``` 
rosrun object_pose_estimation object_pose_estimation_ros
```

**Visualize on Rviz**
visualize topic on `/scan`, `/target_pose`, `/target_cloud`.
```
rviz -f laser
```


## What's Going on
Via hokoyu scan input, convert to pointcloud, use ransac line detector to find the target flat object, then find the boundary of the line, at last estimate the pose of the detected object.

## Some Back Up Code
PCL Ransac line fitting
```
cd pcl_ransac/build
cmake ..
make -j4
./random_sample_consensus -input <input.pcd>
```
