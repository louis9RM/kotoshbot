cmake_minimum_required(VERSION 3.10)
project(kotoshbot_base)

find_package(ament_cmake REQUIRED)

# Si quieres ya declarar dependencias (aunque no se usen aún):
find_package(rclcpp REQUIRED)
find_package(std_srvs REQUIRED)

ament_package()
