cmake_minimum_required(VERSION 3.8)
project(kotoshbot_base)

# Dependencias necesarias
find_package(ament_cmake REQUIRED)
find_package(hardware_interface REQUIRED)
find_package(pluginlib REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rclcpp_lifecycle REQUIRED)
find_package(std_srvs REQUIRED)

# Incluye todas las cabeceras del paquete
include_directories(include)

# 1) Crear librería con tu código de infraestructura/hardware
add_library(kotoshbot_hardware SHARED 
          src/infrastructure/hardware/DEV_Config.c
)
target_include_directories(kotoshbot_hardware PRIVATE include)





add_executable(kotoshbot_node src/main.cpp)
ament_target_dependencies(kotoshbot_node rclcpp)

install(TARGETS
  kotoshbot_node
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()
