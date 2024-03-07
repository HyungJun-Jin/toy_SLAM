# 3D Position and Rotation Practice 
1. [Eigen basics](https://eigen.tuxfamily.org/dox/) (Eigen matrices and vectors)
2. Rotations (SO(3), Angle-axis, quaternions) - Using Eigen3
3. Visualize 3D coordinates (Pangolin)


## Rotation method
### Euler Angle, SO(3), Axis-Angle, Quaternion
- Euler Angle : Yaw, pitch, roll (Sequence is important)  
- SO(3) : Special Orthogonal Matirx (3D)  
$SO(3) = \{ R \in \mathbb{R}^{3\times3} | R^TR=I, det(R)=1\}$  
- Axis-Angle  
$\mathbb{\theta} = \theta\mathrm{e}$ ($\mathrm{e}$=unit vector)
- Quaternion : add complex number concept  
$q = w +ix+ jy + kz$  
$i^2=j^2=k^2=ijk=-1$  
$ij=k, jk=i, ki=j, ji=-k, kj=-i, ik=-j$  

### SE(3)
Special Euclidean Group (3D): SO(3) + Translation($t_x, t_y, t_z$)  
$SE(3) = \{ T=
\begin{bmatrix}
\ R & t \\
\ 0^T & 1
\end{bmatrix}
\in \mathbb{R}^{4\times4}| R \in SO(3), t\in\mathbb{R}^3
\}$  -> ⭐4 by 4 matrix  

## 3D pose viewer
3D coordinate viewer (KITTI dataset pose format = 1camera)

3D coordinates (11501 coordinates)  
= 11501 * SE(3) Matrix  
= 11501 * [index, R11, R12, R13, t14, R21, R22, R23, t24, R31, R32, R33, t34, 0, 0, 0, 1]  
= 11501 * $\begin{bmatrix}
\ R & t \\
\ 0^T & 1
\end{bmatrix}$

👇 cam0_to_world.txt => SE(3) values 👇
![](./img/cam0_data.png)
👇 Visualize 👇
![](./img/3d_pose_viewer.gif)


### Build 
Pre-requisite: Eigen3, Pangolin v0.6

### Run (Local)

```
./build/pose_viewer ./cam0_to_world.txt
```


### Run (Docker)

```
# Enable docker port for visualization
xhost +local:docker

# Build and run docker image (X11: GUI port fowarding)
docker build . -t ubuntu_focal:3D_Position_Rotation
docker run -it --env DISPLAY=$DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix:ro ubuntu_focal:3D_Position_Rotation

# Inside docker
cd ./3D_Position_Rotation
./build/pose_viewer ./cam0_to_world.txt
```

