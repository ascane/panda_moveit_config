cmake_minimum_required(VERSION 3.4)
project(panda_moveit_config)
find_package(catkin REQUIRED COMPONENTS gazebo_msgs roscpp geometry_msgs std_srvs std_msgs message_generation)

generate_messages(DEPENDENCIES std_msgs)
catkin_package(CATKIN_DEPENDS message_runtime)

install(DIRECTORY launch DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  PATTERN "setup_assistant.launch" EXCLUDE)
install(DIRECTORY config DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})


# Specify locations of header files.
include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(blocks_spawner blocks_spawner.cpp)
target_link_libraries(blocks_spawner ${catkin_LIBRARIES})
