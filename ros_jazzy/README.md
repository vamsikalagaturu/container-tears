# ROS Jazzy Desktop

- Image: `osrf/ros:jazzy-desktop`
- Host : Arch+Wayland
- GPU  : Nvidia

## Requires .env

```.env
USERNAME=<USERNAME>
UID=<UID>
GID=<GID>
```

## To Note:

- Maps host UID and GID to the container
- Runs on host network
- Mounts host's `$HOME` to the container
- Access to host's `/dev`
- Below two might be useful incase of issues with clipboard-copy and QT apps

  ```shell
  xhost +local:root

  export QT_QPA_PLATFORM=xcbexport QT_QPA_PLATFORM=xcb
  ```
