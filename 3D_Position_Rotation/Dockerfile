FROM slam:3d_position_rotation 

RUN cd toy_SLAM/3D_Position_Rotation &&\
    mkdir build && cd build && \
    cmake -GNinja ../ && \
    ninja -j4