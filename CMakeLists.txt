cmake_minimum_required(VERSION 2.8.3)

project(nite2)

find_package(orocos_kdl REQUIRED)
find_package(catkin REQUIRED COMPONENTS geometry_msgs
					roscpp
					roslib
					tf)
find_package( OpenCV REQUIRED )



include_directories(${catkin_INCLUDEDIR})

link_directories(${catkin_LIBRARY_DIRS})

set(OPENNI2_DIR /home/baidu/OpenNI-Linux-x64-2.2)
set(NITE2_DIR /home/baidu/NiTE-2.0.0/)
set(NITE2_LIB /home/baidu/NiTE-2.0.0/Redist)


link_directories(${OPENNI2_DIR}/Bin/x64-Release)

include_directories(${OPENNI2_DIR}/Bin/x64-Release)
include_directories(/usr/include/openni2/)
include_directories(${OPENNI2_DIR}/Include)
include_directories(${NITE2_DIR}/Include)
include_directories(${OpenCV_INCLUDE_DIRS}/include)
include_directories(/home/baidu/NiTE-2.0.0/Redist)

add_executable(Nite2 src/nite2.cpp)
target_link_libraries(Nite2 OpenNI2 ${NITE2_LIB} ${NITE2_LIB}/libNiTE2.so ${OpenCV_LIBRARIES} ${catkin_LIBRARIES})
