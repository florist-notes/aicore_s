# Nav2 stack  :ros 2

The ROS 2 Navigation Stack is a set of packages and tools that enable mobile robots to autonomously navigate through their environment. It provides capabilities like obstacle avoidance, path planning, and localization, allowing robots to move safely and efficiently. Below is a detailed technical description of the key components of the ROS 2 Navigation Stack with example code snippets.

`Costmaps`: Costmaps are grid-based representations of the robot's environment that help it navigate around obstacles. The ROS 2 Navigation Stack uses two costmaps: the global costmap (for long-term planning) and the local costmap (for short-term, local planning).

```yaml
# costmap_common_params.yaml example
footprint: [[-0.3, -0.3], [-0.3, 0.3], [0.3, 0.3], [0.3, -0.3]]
inflation_radius: 0.55
resolution: 0.05


```

`Global Planner`: The global planner computes a high-level plan from the robot's current position to the goal position, considering the global costmap. One common choice for global planning is the `nav2_navfn_planner`.

```py

# Python code to set up the global planner
from nav2_navfn_planner.navfn_planner import NavfnPlanner

global_planner = NavfnPlanner()
global_planner.configure(node, tf, costmap, "GlobalPlanner")
```

`Local Planner`: The local planner generates low-level velocity commands that steer the robot around obstacles using the local costmap. The `nav2_dwa_local_planner` is a popular choice for this task.

```py

# Python code to set up the local planner
from nav2_dwa_local_planner.dwa_planner import DWAPlanner

local_planner = DWAPlanner()
local_planner.configure(node, tf, costmap, "LocalPlanner")


```


`Trajectory Planner`: The trajectory planner generates feasible trajectories that the robot can follow based on its kinematic constraints.

```py

# Python code to set up the trajectory planner
from nav2_common.trajectory_planner import TrajectoryPlanner

trajectory_planner = TrajectoryPlanner()
trajectory_planner.configure(node, tf, costmap, local_planner, "TrajectoryPlanner")


```



`Behavior Tree`: To orchestrate the navigation process, a behavior tree is often used. The behavior tree coordinates the actions of the global and local planners, monitors progress, and handles recovery behaviors.

```py

# Python code to set up the behavior tree
from nav2_behavior_tree import BehaviorTreeEngine

bt_engine = BehaviorTreeEngine(local_planner, global_planner, trajectory_planner)

```

`Navigation Stack Node`: A ROS 2 node is responsible for tying all the components together and executing the navigation tasks. It subscribes to a goal pose, updates the costmaps, and triggers the behavior tree.

```py

# Python code to create the navigation stack node
from nav2_system_tests.test_behavior_tree import Nav2BehaviorTreeFixture

nav2_node = Nav2BehaviorTreeFixture()
nav2_node.configure(bt_engine, costmap, local_costmap, global_costmap)


```


> Install Nav2 on ROS2 Humble > Generate a map with SLAM > Make a robot navigate using the map <br />

 nav2 : [web](https://nav2.org/), [github](https://github.com/ros-planning/navigation2)
 
<img src="./nav.png" width=48%><a> </a><img src="./nav2.png" width=12%><a> </a><img src="./gaz.png" width=22%>

```bash

$ sudo apt install ros-humble-navigation2 ros-humble-nav2-bringup ros-humble-turtlebot3*

```

Turtle Bot 3 : `$ gedit ~/.bashrc`

```bash

export TURTLEBOT3_MODEL=waffle
source /opt/ros/humble/setup.bash


```
next do : `$ source .bashrc` and `$ printenv | grep TURTLE`

### Gazebo : ` $ gazebo` > `$ ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py`

start node :  `$ ros2 run turtlebot3_teleop teleop_keyboard`, also check ` $ rqt_graph`.

 
<img src="./turtlebot.png" width=100%>


## Simultaneous localization and mapping (SLAM)

`$ ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py`

`$ ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True`

Rviz opens up:
<img src="./rviz.png" width=100%>

save map : `$ mkdir maps` > `ros2 run nav2_map_server map_saver_cli -f maps/my_map` : files generated `.pgm` and `.yaml`

nav2 fixes : ` $ sudo apt install ros-humble-rmw-cyclonedds-cpp` > ` $ gedit ~/.bashrc`, add: 

```bash

     $ export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp

```

### Navigation of the Robot : 

`$ ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py`

`$ ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True maps:=maps/my_map.yaml`

Click in RViz : " 2D Pose Estimate "

<img src="./nav_ros.png" width=100%>

resources : [Navigation and SLAM Using the ROS 2 Navigation Stack](https://automaticaddison.com/navigation-and-slam-using-the-ros-2-navigation-stack/), [Sensor Fusion Using the Robot Localization Package – ROS 2](https://automaticaddison.com/sensor-fusion-using-the-robot-localization-package-ros-2/), [LIDAR for a Simulated Mobile Robot in ROS 2](https://automaticaddison.com/set-up-lidar-for-a-simulated-mobile-robot-in-ros-2/)