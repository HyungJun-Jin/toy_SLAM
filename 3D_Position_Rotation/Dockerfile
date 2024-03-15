FROM slam:base

RUN git clone https://github.com/HyungJun-Jin/toy_SLAM.git

RUN cd toy_SLAM/3D_Position_Rotation
RUN mkdir build && cd build
RUN cmake -G Ninja ../ 
RUN ninja -j4