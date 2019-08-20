# TS Double Robot Navigation

TS Double Robot Navigation is a [ROS](http://www.ros.org/) package developed to power Double 2 Robot by [Double Robotics](https://www.doublerobotics.com) to avoid obstacles and in further perspective to navigate autonomously.

## ROS target version

The target version of ROS is [Melodic Morenia](http://wiki.ros.org/melodic) though one may feel free to adjust the package to any other version of ROS.

## Prerequisites

- Ubuntu Bionic is installed. The distribution can be found [here](http://releases.ubuntu.com/18.04/).
- ROS Melodic Morenia is installed. The instructions on how to do that can be found [here](http://wiki.ros.org/melodic/Installation).
- You are familiar with the concepts of ROS such as packages, nodes, topics, services. If you are not it is recommended to address the course [ROS for Beginners: Basics, Motion, and OpenCV](https://www.udemy.com/ros-essentials/) by Prof. Anis Koubaa.
- The catkin workspace is created. If it is not please follow the instructions [here](http://wiki.ros.org/catkin/Tutorials/create_a_workspace).
- Don't forget to add the catkin workspace setup.sh file to your bashrc file
```sh
$ echo 'source ~/catkin_ws/devel/setup.sh' >> ~/.bashrc
$ echo 'echo $ROS_PACKAGE_PATH' >> ~/.bashrc
$ source ~/.bashrc
```
- Git version control system is installed

## Getting started

```sh
$ apt-get install ros-melodic-turtlebot3-*
$ echo 'export TURTLEBOT3_MODEL=waffle' >> ~/.bashrc
$ source ~/.bashrc
$ cd ~/catkin_ws/src
$ git clone https://github.com/LebedkoDmitry/ts-doublerobot-navigation.git
$ cd ..
$ catkin_make
$ apt-get install ros-melodic-slam-gmapping
$ apt-get install ros-melodic-dwa-local-planner
$ apt-get install ros-melodic-rosbridge-server
$ roslaunch ts_doublerobot_navigation ts_doublerobot_navigation.launch
```
### How to run urdf-file

```sh
export LC_NUMERIC="en_US.UTF-8"
roslaunch urdf_tutorial display.launch model:=/path/to/file/double_robotics.urdf
```

### How to set a goal to move to

```sh
rostopic pub /move_base_simple/goal geometry_msgs/PoseStamped '{header: {stamp: now, frame_id: "map"}, pose: {position: {x: 5.0, y: 2.0, z: 0.0}, orientation: {w: 1.0}}}' --once -v
```

### How to deploy

At the moment we do not provide any Docker public images and do not host the package anywhere in public.
