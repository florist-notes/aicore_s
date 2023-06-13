# Robot Operating System ([ROS](https://www.ros.org/)) | [wiki](https://en.wikipedia.org/wiki/Robot_Operating_System)

<img src="../img/ros.png" width=49%><a> </a><img src="../img/rosindustrial.png" width=49%>

full installation @ [docs.ros.org](https://docs.ros.org/en/rolling/Installation/Ubuntu-Install-Debians.html)

```bash
    $ sudo apt update && sudo apt install ros-dev-tools
    $ sudo apt install ros-rolling-desktop
    $ source /opt/ros/rolling/setup.bash (put this in .bashrc / $ gedit ~/.bashrc)

```

The [Robot Operating System (ROS)](https://www.ros.org/) is a set of software libraries and tools that help us build robot applications. From drivers to state-of-the-art algorithms, and with powerful developer tools, ROS has what we need for our next robotics project. And it's all open source. { [awesome/ros2](https://fkromer.github.io/awesome-ros2/) } & [programming multiple robots with ros2](https://osrf.github.io/ros2multirobotbook/intro.html).

<img src="../img/rosdf.png" width=40%><a> </a><img src="../img/rrdd.png" width=57%>

#####  [ROS Framework Overview](https://youtu.be/7TVWlADXwRw) | [ROS 2 : Rolling Ridley](https://docs.ros.org/en/rolling/index.html) | [github/ros2](https://github.com/ros2) | [ETH Z : Programming for Robotics - ROS](https://rsl.ethz.ch/education-students/lectures/ros.html) | [ubuntu/what is ros?](https://ubuntu.com/robotics/what-is-ros) | [ROSCON](https://roscon.ros.org/) | [ROS2 Humble Crash course](https://youtu.be/Gg25GfA456o)

ROS processes are represented as nodes in a graph structure, connected by edges called topics. ROS nodes can pass messages to one another through topics, make service calls to other nodes, provide a service for other nodes, or set or retrieve shared data from a communal database called the parameter server. A process called the ROS Master makes all of this possible by registering nodes to itself, setting up node-to-node communication for topics, and controlling parameter server updates. Messages and service calls do not pass through the master, rather the master sets up peer-to-peer communication between all node processes after they register themselves with the master. This decentralized architecture lends itself well to robots, which often consist of a subset of networked computer hardware, and may communicate with off-board computers for heavy computing or commands. List of ROS [tools](https://en.wikipedia.org/wiki/Robot_Operating_System#Tools), [versions and releases](https://en.wikipedia.org/wiki/Robot_Operating_System#Versions_and_releases) and [configuring your ros2 environment](https://docs.ros.org/en/crystal/Tutorials/Configuring-ROS2-Environment.html).

## ROS 2 Projects:


```bash
 $ ros2 run demo_nodes_cpp talker  ( $ ros2 run package_module nodename )
 $ ros2 run demo_nodes_cpp listener
 $ rqt_graph
 $ ros2 run turtlesim turtlesim_node
 $ ros2 run turtlesim turtle_teleop_key (listen to keystrokes)

```

ros2 workspace:
```bash
 $ sudo apt install python3-colcon-common-extensions
 $ cd /usr/share/colcon_argcomplete/hook/
 $ gedit ~/.bashrc ( source /usr/share/colcon_argcomplete/hook/)
 $ mkdir ros2_ws > $ cd ros2_ws
 $ mkdir src 
 (ros2_ws) $ colcon build > $ ls
 $ gedit ~/.bashrc ( source ~/ros2_ws/install/setup.bash )

```
ros2 application (create packages in src):

```bash

 $ ros2 pkg create my_robot_controller  --build-type ament_
 $ ros2 pkg create my_robot_controller  --build-type ament_python --dependencies rclpy
 $ ls (rclpy in the py package for ros2)

```
'colcon' is the build tool and 'ament' is the build system. We can havr multiple nodes in a package and packages can be dependent on each other. 
##  [ROS Industrial](https://rosindustrial.org/)

ROS-Industrial is an open-source project that extends the advanced capabilities of ROS software to industrial relevant hardware and applications.

## [NVIDIA Issac ROS](https://developer.nvidia.com/isaac-ros)

<img src="../img/esdf.gif" width=41%><a> </a><img src="../img/elbrus_live.gif" width=57%>