cmake_minimum_required(VERSION 3.0.2)
project(w1)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  genmsg
)

generate_messages(DEPENDENCIES
  std_msgs
)

catkin_package()

include_directories(
  include ${catkin_INCLUDE_DIRS}
)

add_executable(talker src/talker.cpp)
target_link_libraries(talker ${catkin_LIBRARIES})
add_dependencies(talker w1_generate_messages_cpp)

add_executable(listener src/listener.cpp)
target_link_libraries(listener ${catkin_LIBRARIES})
add_dependencies(listener w1_generate_messages_cpp)

add_executable(teleop_turtle_key src/teleop_turtle_key.cpp)
target_link_libraries(teleop_turtle_key ${catkin_LIBRARIES})
add_dependencies(teleop_turtle_key w1_generate_messages_cpp)
