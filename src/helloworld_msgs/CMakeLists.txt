cmake_minimum_required(VERSION 2.8.3)
project(helloworld_msgs)

find_package(catkin REQUIRED COMPONENTS std_msgs message_generation)

add_message_files(
  FILES Buttons.msg
)

generate_messages(
  DEPENDENCIES std_msgs
)

catkin_package(
  CATKIN_DEPENDS message_runtime std_msgs
)


