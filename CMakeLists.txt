cmake_minimum_required(VERSION 3.5)

project(px4_msgs)

list(INSERT CMAKE_MODULE_PATH 0 "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
	add_compile_options(-Wall -Wextra)
endif()

find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# ##############################################################################
# Generate ROS messages, ROS2 interfaces and IDL files #
# ##############################################################################

# get all msg files
# set(MSGS_DIR "${CMAKE_CURRENT_SOURCE_DIR}/msg")
# file(GLOB PX4_MSGS RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "${MSGS_DIR}/*.msg")
# 
# file(GLOB ROS_MSG_DIR_LIST "${MSGS_DIR}/*.msg")
# 
# set(ROS_MSG_DIR_LIST "${ROS_MSG_DIR_LIST}" CACHE INTERNAL "ROS_MSG_DIR_LIST")

set(PX4_MSGS 
  "msg/DebugVect.msg"
  "msg/ActionRequest.msg"
  "msg/CollisionConstraints.msg"
  "msg/FailsafeFlags.msg"
  "msg/SensorCombined.msg"
  "msg/TimesyncStatus.msg"
  "msg/VehicleAngularVelocity.msg"
  "msg/VehicleAttitude.msg"
  "msg/VehicleControlMode.msg"
  "msg/VehicleGlobalPosition.msg"
  "msg/SensorGps.msg"
  "msg/VehicleLocalPosition.msg"
  "msg/VehicleOdometry.msg"
  "msg/VehicleStatus.msg"
  "msg/OffboardControlMode.msg"
  "msg/OnboardComputerStatus.msg"
  "msg/ObstacleDistance.msg"
  "msg/SensorOpticalFlow.msg"
  "msg/TelemetryStatus.msg"
  "msg/TrajectorySetpoint.msg"
  "msg/VehicleAttitudeSetpoint.msg"
  "msg/VehicleRatesSetpoint.msg"
  "msg/VehicleCommand.msg"
  "msg/TrajectoryWaypoint.msg"
  "msg/TrajectoryBezier.msg"
  "msg/VehicleTrajectoryBezier.msg"
  "msg/VehicleTrajectoryWaypoint.msg"
  "msg/CommanderStatus.msg"
  "msg/CommanderSetState.msg"
)

# message(${PX4_MSGS})

# Generate introspection typesupport for C and C++ and IDL files
rosidl_generate_interfaces(${PROJECT_NAME} ${PX4_MSGS}
	DEPENDENCIES builtin_interfaces
	ADD_LINTER_TESTS
)

ament_export_dependencies(rosidl_default_runtime)

ament_package()
