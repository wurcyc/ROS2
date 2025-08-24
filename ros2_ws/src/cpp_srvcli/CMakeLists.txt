cmake_minimum_required(VERSION 3.5)
project(cpp_srvcli)

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(tutorial_interfaces REQUIRED)
find_package(example_interfaces REQUIRED)

add_executable(server src/add_two_ints_server.cpp)
add_executable(server_new src/add_three_ints_server.cpp)
target_link_libraries(server PUBLIC rclcpp::rclcpp ${example_interfaces_TARGETS})
target_link_libraries(server_new PUBLIC rclcpp::rclcpp ${tutorial_interfaces_TARGETS})

add_executable(client src/add_two_ints_client.cpp)
add_executable(client_new src/add_three_ints_client.cpp)
target_link_libraries(client PUBLIC rclcpp::rclcpp ${example_interfaces_TARGETS})
target_link_libraries(client_new PUBLIC rclcpp::rclcpp ${tutorial_interfaces_TARGETS})

install(TARGETS
  server
  client
  server_new
  client_new
  DESTINATION lib/${PROJECT_NAME})

ament_package()
