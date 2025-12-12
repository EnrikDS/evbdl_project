# Base image: ROS 2 Jazzy with desktop tools (includes RViz, rqt, etc.)
FROM ros:jazzy

# Avoid interactive apt prompts
ENV DEBIAN_FRONTEND=noninteractive

# Core dev dependencies
RUN apt-get update && apt-get install -y \
    git \
    build-essential \
    cmake \
    python3-pip \
    python3-colcon-common-extensions \
    python3-vcstool \
    python3-rosdep \
    # MoveIt 2 for Jazzy
    ros-jazzy-moveit \
    # ros2_control 
    ros-jazzy-ros2-control \
    ros-jazzy-ros2-controllers \
    # Handy tools
    nano \
    less \
    && rm -rf /var/lib/apt/lists/*

#RVIZ install
RUN apt-get update
RUN apt-get install -y ros-jazzy-rviz2
# rosdep setup 
RUN rosdep init || true && rosdep update

# ROS environment
# Ensure every shell in the container sources ROS
SHELL ["/bin/bash", "-lc"]
RUN echo "source /opt/ros/jazzy/setup.bash" >> /root/.bashrc

# Default workspace
WORKDIR /workspace/evbdl_ws
# VS Code will mount your local folder here, so this becomes your ROS2 workspace root
