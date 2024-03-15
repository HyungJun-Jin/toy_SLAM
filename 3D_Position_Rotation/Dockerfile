FROM slam:base

RUN git clone https://github.com/HyungJun-Jin/toy_SLAM.git &&\
    cd toy_SLAM/3D_Position_Rotation &&\
    mkdir build && cd build &&\
    cmake -G Ninja ../ &&\
    ninja -j4