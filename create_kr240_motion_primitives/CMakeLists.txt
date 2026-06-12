cmake_minimum_required(VERSION 3.16)
project(create_kr240_motion_primitives LANGUAGES CXX)

if(CMAKE_CXX_COMPILER_ID MATCHES "(GNU|Clang)")
  add_compile_options(-Wall -Wextra)
endif()

set(THIS_PACKAGE_INCLUDE_DEPENDS
  controller_manager
  rclcpp
)

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(backward_ros REQUIRED)
foreach(Dependency IN ITEMS ${THIS_PACKAGE_INCLUDE_DEPENDS})
  find_package(${Dependency} REQUIRED)
endforeach()

install(
  DIRECTORY config launch rviz
  DESTINATION share/create_kr240_motion_primitives
)

ament_export_dependencies(${THIS_PACKAGE_INCLUDE_DEPENDS})
ament_package()
