FROM slam:base 

RUN cd toy_SLAM/3D_Position_Rotation &&\
    mkdir build && cd build && \
    cmake -G Ninja ../ && \
    ninja -j4