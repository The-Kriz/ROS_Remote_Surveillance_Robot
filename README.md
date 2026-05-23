# ROS Remote Surveillance Robot

An autonomous indoor surveillance robot built on ROS2, capable of real-time threat
detection and autonomous navigation. Features a deep learning vision pipeline for
anomaly and weapon detection, SLAM-based mapping, and remote monitoring via live
camera feed.

[![ROS2](https://img.shields.io/badge/ROS2-Humble-blue)](https://docs.ros.org/en/humble/)
[![License](https://img.shields.io/badge/License-Apache_2.0-green)](LICENSE.md)

---

## Demo

> 📸 RViz + Gazebo screenshots, real world testing videos → https://tinyurl.com/Remote-Surveillance-Robot

| Full Robot (RViz) | Gazebo Simulation | Physical Build |
|---|---|---|
| ![rviz pic](https://github.com/The-Kriz/rog_ros_bot/assets/90817926/cbf302e6-66fe-47a0-bc24-b182f577a467) | ![gazebo](https://github.com/The-Kriz/rog_ros_bot/assets/90817926/12e0c792-45bc-40ff-9b38-798369b841f1) | ![real 1](https://github.com/The-Kriz/rog_ros_bot/assets/90817926/10a06eaa-d31e-443d-a39c-ca5b8477389d) |

---

## What I Built

This is a full-stack robotics project — hardware design, embedded firmware, ROS2
software, and AI perception all built from scratch:

- **Custom PCB (Altium Designer)** — Designed the robot's motor driver and power
  management board from scratch in Altium. Gerber files included. This
  replaced off-the-shelf boards and allowed direct integration with the onboard compute.

- **Custom mechanical design (SolidWorks)** — Designed the full chassis and sensor
  mount in SolidWorks. Supports two interchangeable wheel configurations: standard
  skid-steer wheels and mecanum wheels for omnidirectional movement.

- **Dual drive configurations** — The robot supports both a standard skid-steer
  wheel setup and a mecanum/omni wheel setup, each with its own kinematics node.
  This was a deliberate design choice to test different navigation behaviours.

- **Skid-steer drive kinematics** — Implemented a ROS2 differential drive node
  handling encoder-based odometry and motor velocity commands.

- **SLAM-based autonomous navigation** — Integrated SLAM Toolbox with Nav2 for
  real-time indoor mapping and autonomous path planning. The occupancy grid map
  below was generated from a live LiDAR scan on physical hardware.

- **Deep learning vision pipeline** — Integrated a YOLO-based object detection
  model for real-time anomaly and weapon detection from the onboard camera feed.
  Detection results are published as ROS2 topics for downstream alerting.

- **Remote monitoring interface** — Camera feed and robot telemetry streamed over
  the network for remote operation and live surveillance.

---

## System Architecture

<img width="700" alt="System Architecture" src="https://github.com/user-attachments/assets/eeed2adf-ff8d-4ab5-af23-a6ad1cfc76c2" />

---

## Hardware

| Component    | Details                              |
|--------------|--------------------------------------|
| Compute      | Jetson & Desktop             |
| LiDAR        | RPLidar A1                           |
| Camera       | Intel RealSense                      |
| IMU          | MPU6050                              |
| Motor Driver | Custom PCB designed in Altium        |
| Drive        | Skid-steer / Mecanum (swappable)     |
| Chassis      | Custom SolidWorks design, 3D printed |

---

## SLAM in Action (Real Hardware)

The map below was generated live on the physical robot — not in simulation.

<img width="700" alt="SLAM map" src="https://github.com/user-attachments/assets/35552d22-fcc8-4f3f-a73e-bd0765570757" />

---

## PCB Design (Altium Designer)

Custom motor driver and power management board. Gerber files available in `/pcb`.

<img width="600" alt="PCB Layout" src="https://github.com/user-attachments/assets/610c98ef-462e-4975-8bba-7ef9144fe918" />

---

## Drive Configurations

The chassis supports two interchangeable wheel setups, each with a corresponding
ROS2 kinematics node:

| Standard Skid-Steer | Mecanum / Omni Wheels |
|---|---|
| <img width="420" alt="Normal wheel" src="https://github.com/user-attachments/assets/022a7a7b-e2e6-491f-8917-2113e1fe650e" /> | <img width="420" alt="Mecanum wheel" src="https://github.com/user-attachments/assets/cc0a669e-d950-4204-8f7f-f0787b6c9d35" /> |

---

## CAD Design

| View 1 | View 2 | View 3 |
|--------|--------|--------|
| <img width="280" alt="cad1" src="https://github.com/The-Kriz/rog_ros_bot/assets/90817926/97e8e0a6-08bc-4487-9f2c-c48c43e096ba" /> | <img width="280" alt="cad2" src="https://github.com/user-attachments/assets/2018176e-a0e7-41ca-b1c4-dc35f0fcad60" /> | <img width="280" alt="cad3" src="https://github.com/The-Kriz/rog_ros_bot/assets/90817926/2c37552a-216d-4e06-966d-ef815a751a47" /> |

---

## Physical Build

| Build 1 | Build 2 | Build 3 |
|---------|---------|---------|
| <img width="280" alt="build1" src="https://github.com/The-Kriz/rog_ros_bot/assets/90817926/10a06eaa-d31e-443d-a39c-ca5b8477389d" /> | <img width="280" alt="build2" src="https://github.com/The-Kriz/rog_ros_bot/assets/90817926/e106d1be-d787-4cfa-99ea-35f55aadef9d" /> | <img width="280" alt="build3" src="https://github.com/The-Kriz/rog_ros_bot/assets/90817926/6fb5654f-f8e2-472e-9dde-2ce16b72dd1f" /> |

---

## Getting Started

### Prerequisites
- ROS2 Humble
- Nav2
- SLAM Toolbox
- OpenCV
- PyTorch / TensorFlow (for detection node)

### Build

```bash
mkdir -p ~/surveillance_ws/src && cd ~/surveillance_ws/src
git clone https://github.com/The-Kriz/ROS_Remote_Surveillance_Robot
cd ..
colcon build --symlink-install
source install/setup.bash
```

### Run

**Simulation:**
```bash
ros2 launch rog_ros_bot launch_sim.launch.py use_sim_time:=true
```

**Navigation + SLAM:**
```bash
ros2 launch rog_ros_bot navigation.launch.py
```

**Surveillance / Detection:**
```bash
ros2 launch rog_ros_bot surveillance.launch.py
```

---

## Skills Demonstrated

`ROS2` `Nav2` `SLAM` `Deep Learning` `YOLO` `OpenCV` `Altium Designer`
`SolidWorks` `PCB Design` `Embedded C/C++` `Skid-Steer Kinematics` `Mecanum Drive` `Python` `C++`

---

*Part of my robotics portfolio — see also [Project EVA Humanoid Robot](https://github.com/The-Kriz/Project_Eva_Humanoid_Robot)*
