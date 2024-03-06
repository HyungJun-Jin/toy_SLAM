# 3D Position and Rotation Practice 
1. Eigen basics (Eigen matrices and vectors)
2. Rotations (SO(3), Angle-axis, quaternions) - Using Eigen3


## build 

Pre-requisite: Eigen3, Pangolin v0.6


## 3D pose viewer

A simple 3D coordinate viewer. Currently supports KITTI dataset pose format.


### Demo

![](./3d_pose_viewer.gif)


### How to run (Local)

```
./build/pose_viewer ./cam0_to_world.txt
```


### How to run (Docker)

```
# Enable docker port for visualization
xhost +local:docker

# Build and run docker image
docker build . -t slam:2_2
docker run -it --env DISPLAY=$DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix:ro slam:2_2

# Inside docker
cd fastcampus_slam_codes/2_2
./build/pose_viewer ./cam0_to_world.txt
```

