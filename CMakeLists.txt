cmake_minimum_required(VERSION 2.8.3)
project(microstrain_3dm_gx3_35)

find_package(catkin REQUIRED COMPONENTS roscpp sensor_msgs tf geometry_msgs)

catkin_package()

include_directories(include ${catkin_INCLUDE_DIRS})

add_library(3dmgx3_35 src/driver.cpp)

add_executable(imu_driver src/node.cpp)
target_link_libraries(imu_driver 3dmgx3_35 ${catkin_LIBRARIES})

roslaunch_add_file_check(launch)