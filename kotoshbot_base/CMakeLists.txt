cmake_minimum_required(VERSION 3.8)
project(kotoshbot_base)

# Reglas de compilación (warning pero permitir C++)
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_srvs REQUIRED)

# ---- BUILD ----
add_library(${PROJECT_NAME} SHARED
  src/application/
  src/domain/
  src/infrastructure/hardware/
)

target_include_directories(${PROJECT_NAME} PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

ament_target_dependencies(${PROJECT_NAME}
  rclcpp
  std_srvs
)

# ---- INSTALL ----
install(
  DIRECTORY include/
  DESTINATION include
)

# ---- EXPORT ----
ament_export_dependencies(rclcpp std_srvs)
ament_export_include_directories(include)

ament_package()
