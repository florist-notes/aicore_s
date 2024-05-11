# ROS2 Nav2 | SLAM :

Grid SLAM : slam_toolbox is a grid_map based approach.

For TF Frames - Odom (Odometry Origin) & map "World/global" origin* teh relevant Topics are : [/odom] (nav_msgs/msg/Odometry) [same position info as odom → base_link TF ; velocity, covariances] & [/map] (nav_msgs/msg/OccupancyGrid) [grid map occupancy data]

Install slam_toolbox : ` $ sudo apt install ros-foxy-slam-toolbox `.

robot_core.xacro: [github.com/robot_core.xacro](https://github.com/joshnewans/articubot_one/blob/main/description/robot_core.xacro)

```bash
    $ cp /opt/ros/foxy/share/slam_toolbox/config/mapper_params_online_async.yaml dev_ws/src/articubot_one/config/
```

This copies the following file : [github.com/mapper_params_online_async.yaml](https://github.com/joshnewans/articubot_one/blob/main/config/mapper_params_online_async.yaml). Then to build the file : ` $ colcon build --symlink-install`  → ` $ source install/setup.bash`  → ` $ ros2 launch articubot_one launch_sim.launch.py world:=./src/articubot_one/worlds/obstacles.world`.

To run in Rviz : ` $ rviz2 -d src/articubot_one/config/main.rviz`. Then,

` $ ros2 launch slam_toolbox online_async_launch.py params_file:=./src/articubot_one/config/mapper_params_online_async.yaml use_sim_time:=true` :

online_async_launch.py :
```python
import os

from launch import LaunchDescription
from launch.actions import DeclareLaunchArgument, LogInfo
from launch.conditions import UnlessCondition
from launch.substitutions import LaunchConfiguration, PythonExpression
from launch_ros.actions import Node
from ament_index_python.packages import get_package_share_directory
from nav2_common.launch import HasNodeParams


def generate_launch_description():
    use_sim_time = LaunchConfiguration('use_sim_time')
    params_file = LaunchConfiguration('params_file')
    default_params_file = os.path.join(get_package_share_directory("articubot_one"),
                                       'config', 'mapper_params_online_async.yaml')

    declare_use_sim_time_argument = DeclareLaunchArgument(
        'use_sim_time',
        default_value='true',
        description='Use simulation/Gazebo clock')
    declare_params_file_cmd = DeclareLaunchArgument(
        'params_file',
        default_value=default_params_file,
        description='Full path to the ROS2 parameters file to use for the slam_toolbox node')

    # If the provided param file doesn't have slam_toolbox params, we must pass the
    # default_params_file instead. This could happen due to automatic propagation of
    # LaunchArguments. See:
    # https://github.com/ros-planning/navigation2/pull/2243#issuecomment-800479866
    has_node_params = HasNodeParams(source_file=params_file,
                                    node_name='slam_toolbox')

    actual_params_file = PythonExpression(['"', params_file, '" if ', has_node_params,
                                           ' else "', default_params_file, '"'])

    log_param_change = LogInfo(msg=['provided params_file ',  params_file,
                                    ' does not contain slam_toolbox parameters. Using default: ',
                                    default_params_file],
                               condition=UnlessCondition(has_node_params))

    start_async_slam_toolbox_node = Node(
        parameters=[
          actual_params_file,
          {'use_sim_time': use_sim_time}
        ],
        package='slam_toolbox',
        executable='async_slam_toolbox_node',
        name='slam_toolbox',
        output='screen')

    ld = LaunchDescription()

    ld.add_action(declare_use_sim_time_argument)
    ld.add_action(declare_params_file_cmd)
    ld.add_action(log_param_change)
    ld.add_action(start_async_slam_toolbox_node)

    return ld

```

To list the services available : ` $ ros2 service list`. Save Map (for external use) and Serialize map (for reuse within ros2) from ros2 plugin. [Save Map] saves two files `my_map_save.pgm` and `my_map_save.yaml`. [Serialize Map] saves two files `my_map_serial.data` and `my_map_serial.posegraph`.

To save the map: ` $ `.

resources : [Easy SLAM with ROS using slam_toolbox](https://youtu.be/ZaiA3hWaRzE?si=rN1tTIZ1yEmvJGL1)