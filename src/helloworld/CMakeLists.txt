cmake_minimum_required(VERSION 2.8.3)
project(helloworld)

find_package(catkin REQUIRED COMPONENTS
  rosserial_arduino
  rosserial_client
  helloworld_msgs
)

catkin_package()

rosserial_generate_ros_lib(
  PACKAGE rosserial_arduino
  SCRIPT make_libraries.py
)
add_dependencies(${PROJECT_NAME}_ros_lib ${catkin_EXPORTED_TARGETS})

rosserial_configure_client(
  DIRECTORY firmware
  TOOLCHAIN_FILE ${ROSSERIAL_ARDUINO_TOOLCHAIN}
)

rosserial_add_client_target(firmware hello ALL)
rosserial_add_client_target(firmware hello-upload)
