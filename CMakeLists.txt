cmake_minimum_required(VERSION 2.8.3)
project(gazebo_poltergeist_gimbal)

add_definitions(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  gazebo_ros
)

find_package(gazebo REQUIRED)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${GAZEBO_CXX_FLAGS}")

link_directories(${GAZEBO_LIBRARY_DIRS})
include_directories(${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS})

catkin_package(
  CATKIN_DEPENDS
    roscpp
    gazebo_ros
  LIBRARIES gazebo_poltergeist_gimbal_plugin
)

add_library(gazebo_poltergeist_gimbal_plugin src/gazebo_poltergeist_gimbal_plugin.cpp)
target_link_libraries(gazebo_poltergeist_gimbal_plugin ${catkin_LIBRARIES} ${GAZEBO_LIBRARIES})

install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

install(DIRECTORY resources
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
