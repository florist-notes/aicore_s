# ROS 2 : Unified Robot Description Format (URDF)

ROS 2 (Robot Operating System 2) Universal Robot Description Format (URDF) serves as a fundamental tool for describing robotic systems in a standardized XML format. Let's delve deeper into the components of a URDF file with examples:

### 🌸 Links:
+ `Definition`: Links represent the physical components or rigid bodies of the robot.
+ `Example`: Consider a simple two-link robot arm. Each link is defined in the URDF with attributes such as name, geometry (visual and collision), inertial properties, and reference frames.
 ```xml
 <link name="link1">
    <visual>
        <geometry>
            <box size="0.1 0.1 0.4"/>
        </geometry>
    </visual>
    <collision>
        <geometry>
            <box size="0.1 0.1 0.4"/>
        </geometry>
    </collision>
    <inertial>
        <!-- inertial properties -->
    </inertial>
</link>
 ```
### 🌸 Joints:

+ `Definition`: Joints define the kinematic connections between links, specifying their relative motion.
+ `Example`: In the two-link robot arm example, a revolute joint connects the two links, allowing rotational motion along the z-axis.
  
```xml
<joint name="joint1" type="revolute">
<parent link="link1"/>
<child link="link2"/>
<origin xyz="0 0 0.2" rpy="0 0 0"/>
<axis xyz="0 0 1"/>
<limit lower="-3.1416" upper="3.1416"/>
</joint>
```
### 🌸 Visual and Collision Properties:
+ `Definition`: Visual properties define how the link appears visually, while collision properties are used for collision detection in simulations.
+ `Example`: In the two-link robot arm, visual and collision properties are defined for each link.

```xml
<visual>
    <geometry>
        <!-- visual geometry -->
    </geometry>
</visual>
<collision>
    <geometry>
        <!-- collision geometry -->
    </geometry>
</collision>
```
### 🌸 Robot Description:

+ `Definition`: The robot description tag encapsulates the entire robot model, including all links and joints.
+ `Example`: The robot description tag contains all the links and joints defined within the URDF.
```xml
<robot name="robot_name">
    <!-- Links and Joints -->
</robot>
```

```xml
    <?xml version="1.0"?>
    <robot name="robot">

            <link>
            </link>

            <joint>
            </joint>

            <link>
            </link>

    </robot>
```
<img src="./img/joints.png" width=100%>

 The `<link name="arm_link">` tag has options to specify three different characteristics : `<visual>`, `<collision>` and `<inertial>`.

 In the `<visual>` tag, we can specify three different characteristics : `<geometry>`, `<origin>` and `<material>`. <br />
The `<collision>` tag is used for Physics collision calculations : `<geometry>` and `<origin>`.

The `<inertial>` tag is also used for physics calculations, about how the links responds to forces. The properties are `<mass>`, `<origin>` and `<inertia>`.

<hr />

The `<joint>` tag :

```xml
    <joint name="arm_joint" type="revolute">
        <parent link="slider_link" />
        <child link="arm_link"> 
        <origin xyz="0.25 0 0.15" rpy="0 0 0" />
        <axis xyz="0 -1 0" />
        <limit lower="0" upper="${pi/ 2}" velocity="100" effort="100" />
    </joint>
```

## Using xacro to make things easier:


Xacro, which stands for XML Macro, is a powerful tool within the Robot Operating System (ROS) ecosystem. It is designed to simplify the process of creating and maintaining complex URDF (Unified Robot Description Format) files, which are XML files used to describe the physical configuration of a robot in terms of its kinematic and dynamic properties. Writing URDF files can become cumbersome and error-prone as the complexity of the robot increases. Xacro alleviates these issues by allowing for the use of macros, variables, and reusable components, making the process more manageable and less repetitive.

```bash
    $ sudo apt install ros-foxy-xacro ros-foxy-joint-state-publisher-gui
```

To enable xacro, add `<robot xmlns:xacro="http://www.ros.org/wiki/xacro">`:

`Macros`: You can define macros using the `<xacro:macro>` tag. A macro can include multiple URDF elements and can accept arguments, making it versatile for creating complex structures.

```xml
<xacro:macro name="link_with_inertial" params="name length radius mass">
  <link name="${name}">
    <visual>
      <geometry>
        <cylinder length="${length}" radius="${radius}" />
      </geometry>
    </visual>
    <inertial>
      <mass value="${mass}" />
      <origin xyz="0 0 0" rpy="0 0 0" />
    </inertial>
  </link>
</xacro:macro>
```

<img src="./img/xacro.png" width=100%>

<img src="./img/xacro2.png" width=100%>

<img src="./img/xacro3.png" width=100%>

We can visualize with Rviz. | [How do we describe a robot? With URDF!](https://youtu.be/CwdbsvcpOHM?si=VQqJcrBY-EZPAJDh), [Creating a rough 3D model of our robot with URDF](https://youtu.be/BcjHyhV0kIs?si=0jZzdozibFmpXwMJ), [Use Xacro (XML Macro) and URDF to Parametrize and Model Robots in ROS and RViz](https://youtu.be/2gAYO_fFSlo?si=e6a8_mL-Mvuj5qMq).




