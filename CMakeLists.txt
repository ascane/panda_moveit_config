cmake_minimum_required(VERSION 3.4)
project(panda_moveit_config)
find_package(catkin REQUIRED COMPONENTS gazebo_msgs roscpp geometry_msgs std_srvs std_msgs message_generation)

#add_message files
add_message_files(FILES blocks_poses.msg)
add_message_files(FILES Tracker.msg)

generate_messages(DEPENDENCIES std_msgs)
catkin_package(CATKIN_DEPENDS message_runtime)

install(DIRECTORY launch DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  PATTERN "setup_assistant.launch" EXCLUDE)
install(DIRECTORY config DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})


# Specify locations of header files.
include_directories(include ${catkin_INCLUDE_DIRS})


add_executable(blocks_spawner blocks_spawner.cpp)
add_executable(cylinder_spawner cylinder_spawner.cpp)
# add_executable(blocks_poses_publisher blocks_poses_publisher.cpp)

target_link_libraries(blocks_spawner ${catkin_LIBRARIES})
target_link_libraries(cylinder_spawner ${catkin_LIBRARIES})
# target_link_libraries(blocks_poses_publisher ${catkin_LIBRARIES})
