cmake_minimum_required(VERSION 2.8.3)
project(sensors_description)

find_package(catkin REQUIRED COMPONENTS
             roscpp
             std_msgs
             sensor_msgs
             geometry_msgs
             gazebo_plugins
tf
)

find_package(gazebo REQUIRED)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES drcsim_gazebo_ros_plugins
  CATKIN_DEPENDS gazebo_plugins
#  DEPENDS system_lib
)

include_directories(
  ${PROJECT_SOURCE_DIR}/include
  ${catkin_INCLUDE_DIRS}
  ${GAZEBO_INCLUDE_DIRS}
)

link_directories(
  ${GAZEBO_LIBRARY_DIRS}
)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${GAZEBO_CXX_FLAGS}")

## Declare a cpp library
add_library(MultiSenseSLPlugin src/MultiSenseSLPlugin.cpp)
#target_link_libraries(MultiSenseSLPlugin ${catkin_LIBRARIES})
