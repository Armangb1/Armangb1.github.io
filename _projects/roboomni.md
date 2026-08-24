---
title: "RoboOmni"
description: "ROS 2 Jazzy workspace for a mecanum-wheeled dataset-collection robot with custom ros2_control stack, micro-ROS/ESP32 integration, and synchronized multi-sensor data collection."
date: 2024-11-01
tech: ["ROS 2", "Python", "C++", "Mecanum Drive", "Micro-ROS", "ros2_control", "Robotics", "SLAM", "LiDAR", "RGB-D"]
link: "https://github.com/Armangb1/roboomni"
---

RoboOmni is a ROS 2 (Jazzy) mobile robotics platform built on a mecanum-wheeled chassis for collecting synchronized multimodal datasets (RGB-D, LiDAR, IMU, wheel odometry). The system is engineered end-to-end: a custom `ros2_control` hardware interface talks to an ESP32 via **micro-ROS**, custom **mecanum Jacobian controller** plugins handle the inverse kinematics, and a single launch file brings up sensors, control, and visualization.

Key features include mecanum omnidirectional drive with 4 independently driven wheels for holonomic motion, a custom control stack with `ros2_control` hardware interface and Jacobian/inverse-Jacobian controller plugins, embedded integration via ESP32 firmware bridged over micro-ROS (serial agent), and perception sensors including Kinect RGB-D camera, RPLIDAR, and MPU9250 IMU. The design is dataset-oriented with synchronized wheel odometry, IMU, RGB-D, and 2D LiDAR streams for SLAM and perception research.

The workspace uses a modular repository ecosystem with external repositories managed via `vcs`:
- `mecanum_jacobian_controller`: `ros2_control` controller plugins for mecanum Jacobian + inverse-Jacobian kinematics
- `mecanum_hardware_interface`: Custom `ros2_control` system interface with micro-ROS and UDP hardware implementations
- `mecanum_microros_firmware`: ESP32 firmware for motor control, encoders, MPU9250, FreeRTOS tasks over micro-ROS
- `mecanum_udp_firmware`: Alternate ESP32 firmware and UDP bridge variant

The architecture flows from `cmd_vel` → Jacobian controller → per-wheel voltage → hardware interface → firmware, while odometry and IMU data flow bottom-up back to controllers. A single-command bringup (`ros2 launch mecanum_bringup system_bringup.launch.py`) with conditional launch arguments enables/disables each subsystem (Kinect, LiDAR, micro-ROS, ros2_control, RViz visualization).