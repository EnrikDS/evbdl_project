# evbdl_project
Robot unscrewing bolts in ROS2


# Execute this on the host to allow docker access X server 
xhost +local:docker

# Also on the host execute to know the display number

echo $DISPLAY

# Run the docker image
docker run -it --rm \
  --name evbdl-dev \
  --network host \
  -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix:rw \
  -v ~/Code/evbdl_project/evbdl_ws:/workspace/evbdl_ws \
  -w /workspace/evbdl_ws \
  evbdl-ros2-jazzy \
  bash

  # Inside the container shell verify we can access screen. It should provide same display number as host. 
  echo $DISPLAY