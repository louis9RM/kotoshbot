cmake_minimum_required(VERSION 3.8)
project(kotoshbot_base)

# Dependencias necesarias
find_package(ament_cmake REQUIRED)
#find_package(hardware_interface REQUIRED)
#find_package(pluginlib REQUIRED)
find_package(rclcpp REQUIRED)
#find_package(rclcpp_lifecycle REQUIRED)
find_package(std_srvs REQUIRED)

# Crear la librería (infraestructura/hardware)
#add_library(kotoshbot_hardware SHARED
  #  src/infrastructure/hardware/DEV_Config.c
#)

# Headers solo visibles para la librería (hexagonal)
target_include_directories(kotoshbot_hardware PRIVATE include)

# Instalar la librería
install(
  TARGETS kotoshbot_hardware
  DESTINATION lib/${PROJECT_NAME}
)

# Instalar headers
install(
  DIRECTORY include/
  DESTINATION include
)

ament_package()
