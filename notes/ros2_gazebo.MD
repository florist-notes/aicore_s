# ROS 2 Gazebo

[ [Gazebo ROS2](https://classic.gazebosim.org/tutorials?tut=ros2_overview), [Gazebo Ignition](https://gazebosim.org/api/gazebo/2.10/index.html) ]

```bash
    $ sudo apt install ros-foxy-gazebo-ros-pkgs
    $ gazebo /usr/share/gazebo-11/worlds/seesaw.world
```
Gazebo uses a similar format to URDF called SDF and Gazebo can convert URDF to SDF.

<img src="./img/gazebo2.png" width=100%>

```bash
    $ ros2 launch gazebo_ros gazebo.launch.py
```

To spawn our robot (URDF) to Gazebo:
```bash
    $ ros2 run gazebo_ros spawn_entity.py -topic robot_description -entity mybot
    $ ros2 launch urdf_example rsp_sim.launch.py
    $ ros2 launch urdf_example rsp_sim.launch.py world:=~/my_world.world
```

gazebo collapses all the fixed joints into a single entity. To add cameras in gazebo world, we have to add optical_camera link in the xacro file.

```xml
    <gazebo reference="camera_link">
        <sensor type="depth" name="my_camera">
            <update_rate>20</update_rate>
            <visualize>true</visualize>
            <camera name="cam"></camera>
            <plugin name="camera_controller" filename="libgazebo_ros_camera.so">
            </plugin>
        </sensor>
    </gazebo>
```

<img src="./img/gaz_world.png" width=100%>

Resources : [Simulating Robots with Gazebo and ROS ](https://youtu.be/laWn7_cj434?si=IiQRkcDOkuqvaQrk), [Driving your virtual robot!](https://youtu.be/IjFcr5r0nMs?si=RC_vNRPyOH3L-FVD)

## Driving our virtual robot in Gazebo:

```bash
    $ cd dev_ws/
    $ source install/setup.bash
    $ ros2 launch articubot_one rsp.launch.py use_sim_time:=true
    $ ros2 param get /robot_state_publisher use_sim_time
```

```bash
    $ ros2 launch gazebo_ros gazebo.launch.py
```
```bash
    $ ros2 run gazebo_ros spawn_entity.py -topic robot_description -entity bot_name
```
launch_sim.launch.py: 

```python

import os

from ament_index_python.packages import get_package_share_directory


from launch import LaunchDescription
from launch.actions import IncludeLaunchDescription
from launch.launch_description_sources import PythonLaunchDescriptionSource

from launch_ros.actions import Node



def generate_launch_description():


    # Include the robot_state_publisher launch file, provided by our own package. Force sim time to be enabled
    # !!! MAKE SURE YOU SET THE PACKAGE NAME CORRECTLY !!!

    package_name='articubot_one' #<--- CHANGE ME

    rsp = IncludeLaunchDescription(
                PythonLaunchDescriptionSource([os.path.join(
                    get_package_share_directory(package_name),'launch','rsp.launch.py'
                )]), launch_arguments={'use_sim_time': 'true'}.items()
    )

    # Include the Gazebo launch file, provided by the gazebo_ros package
    gazebo = IncludeLaunchDescription(
                PythonLaunchDescriptionSource([os.path.join(
                    get_package_share_directory('gazebo_ros'), 'launch', 'gazebo.launch.py')]),
             )

    # Run the spawner node from the gazebo_ros package. The entity name doesn't really matter if you only have a single robot.
    spawn_entity = Node(package='gazebo_ros', executable='spawn_entity.py',
                        arguments=['-topic', 'robot_description',
                                   '-entity', 'my_bot'],
                        output='screen')



    # Launch them all!
    return LaunchDescription([
        rsp,
        gazebo,
        spawn_entity,
    ])

```

Combining everything into one ros file : `    $ ros2 launch articubot_one launch_sim.launch.py`.

