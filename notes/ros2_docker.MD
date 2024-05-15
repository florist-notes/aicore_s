# ROS2 Docker 🐋

To set up a ROS 2 development environment with Docker, follow these steps:

+ `Install Docker`: Install Docker on your development machine by following the instructions provided on the official Docker website (https://docs.docker.com/get-docker/).

+ `Create a Dockerfile`: Create a Dockerfile in the root directory of your ROS 2 project. The Dockerfile defines the steps for building a Docker image containing your ROS 2 application and its dependencies. Below is an example Dockerfile for a basic ROS 2 application:

```docker
FROM ros:foxy

# Install additional dependencies
RUN apt-get update && apt-get install -y \
    ros-foxy-navigation2 \
    ros-foxy-cartographer \
    && rm -rf /var/lib/apt/lists/*

# Copy ROS 2 package into container
COPY . /workspace/src/my_ros_package

# Build ROS 2 package
RUN . /opt/ros/foxy/setup.sh && \
    cd /workspace && \
    colcon build --packages-select my_ros_package
```
Build Docker Image: Use the Docker build command to build a Docker image from the Dockerfile:
`$ docker build -t my_ros_image .`.

Run Docker Container: Once the Docker image is built, you can run a Docker container using the following command: `$ docker run -it --rm my_ros_image`.

This command starts a new Docker container based on the `my_ros_image` image and opens an interactive terminal (`-it`). The `--rm` option ensures that the container is removed automatically when it is stopped.

video series : [ [Docker for Robotics Pt 1 - What and Why??](https://youtu.be/XcJzOYe3E6M?si=9na0grJoHc8dK1Vv), [Docker 101](https://youtu.be/SAMPOK_lazw?si=kUAMwaEbljEzxyWF), [Crafting your Dockerfile (Docker and Robotics Pt 3)](https://youtu.be/RbP5cARP-SM?si=C6J_wMDCMUuVNCKs), [Devices in Docker - Not so simple! (Docker for Robotics #4)](https://youtu.be/uf4zOigzTFo?si=4K_-iSuCYaZuunmy), [If you're not developing with this, you're wasting your time](https://youtu.be/dihfA7Ol6Mw?si=kwvY66oqEhPkY0IA), [When your webcam isn't working](https://youtu.be/JIGO3b-aoz8?si=gJmBNClO9QtHChqm) ]