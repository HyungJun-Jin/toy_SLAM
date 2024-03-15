cmake_minimum_required(VERSION 2.8)
project(3D_Position_Rotation)
set(CMAKE_CXX_STANDARD 17)


find_package(Pangolin REQUIRED)
if (${Pangolin_FOUND})
    message(STATUS "Found Pangolin - ${Pangolin_DIR}")

    include_directories(${Pangolin_INCLUDE_DIRS})
    set(PANGOLIN_LIBS ${Pangolin_LIBRARIES})

else (${Pangolin_FOUND})
    message(STATUS "Could not support Pangolin")
endif (${Pangolin_FOUND})

# Pangolin already has Eigen3
# find_package(Eigen3 REQUIRED)


# Executable
add_executable(pose_viewer src/pose_viewer.cpp)
target_link_libraries(pose_viewer ${Pangolin_LIBRARIES})
