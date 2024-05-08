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