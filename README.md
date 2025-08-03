# Outdoor-GPS-Based-Navigation-on-Husky-A200
Outdoor GPS-Based Navigation on Husky A200
# Outdoor GPS-Based Navigation on Husky A200 (Simulation + Real Hardware)

This project demonstrates **outdoor GPS-based navigation** for the **Husky A200** robot, implemented in both simulation and on real hardware.  
The system integrates **GPS, IMU, and odometry** with a **dual-EKF pipeline**, leverages **Cartographer SLAM** for mapping, and uses the **SMAC planner** with **Regulated Pure Pursuit controller** for accurate waypoint navigation.

---

## Features
- **Sensor Fusion**
  - Dual EKF setup using **robot_localization**
  - GPS data processing with **navsat_transform_node**
  - IMU and wheel odometry integration
- **SLAM & Mapping**
  - **Cartographer SLAM** for 2D mapping in outdoor environments
- **Waypoint Navigation**
  - Global path planning using **SMAC Planner**
  - Local path following with **Regulated Pure Pursuit Controller**
  - Achieved waypoint following accuracy of **< 0.5 m**
- **Seamless Mode Switching**
  - Designed reusable launch files for **indoor/outdoor** mode switching
- **Simulation + Hardware Support**
  - Works with **Gazebo** simulation  
  - Fully deployable on **real Husky A200 hardware**

---

## Tools & Technologies
- ROS 2 Humble
- Cartographer SLAM
- Nav2 (SMAC Planner, Regulated Pure Pursuit Controller)
- robot_localization (dual-EKF + navsat_transform_node)
- GPS & IMU
- Gazebo
- C++, Python

---

## Project Structure

├── src/
│ ├── husky_outdoor_navigation/ # Outdoor navigation configuration & launch files
│ ├── husky_description/ # Robot URDF and sensor setup
│ ├── husky_bringup/ # Indoor/outdoor mode launch files
│ └── gps_utils/ # GPS processing and helper scripts
├── maps/ # Maps generated via Cartographer
├── config/ # EKF, Nav2, and Cartographer configs
└── README.md

---

## Installation & Setup

### 1. Prerequisites
- **ROS 2 Humble**
- **Nav2**  
- **Cartographer SLAM**  
- **robot_localization**  
- **GPS & IMU hardware drivers**  

### 2. Clone the Repository
```bash
cd ~/ros2_ws/src
git clone https://github.com/your-username/husky_outdoor_navigation.git
cd ~/ros2_ws
colcon build
source install/setup.bash

ros2 launch husky_bringup outdoor_simulation.launch.py


ros2 launch husky_bringup outdoor_robot.launch.py



ros2 launch husky_outdoor_navigation cartographer_slam.launch.py

ros2 launch husky_outdoor_navigation outdoor_nav2.launch.py waypoints:=config/waypoints.yaml



