---
title: "Development of a Bionic Hexapod Robot with Adaptive Gait and Clearance for Enhanced Agricultural Field Scouting"
permalink: /projects/bionic-hexapod/
author_profile: true
---

<img src="/images/bionic_hexapod.jpg" alt="Bionic hexapod robot" style="width:100%; max-width:850px; border-radius:10px;">

## Overview

This project focuses on the development of a bionic hexapod robot for agricultural field scouting. I designed and built the robot platform from the ground up, including its mechanical structure, leg configuration, sensing layout, and control system integration.

The robot is designed for complex agricultural environments where uneven terrain, dense vegetation, and field obstacles make conventional wheeled platforms less suitable. By using six articulated legs, adaptive gait control, and adjustable body clearance, the robot can traverse uneven terrain and step over obstacles while maintaining stable locomotion.

## Robot Platform Design

The robot uses a lightweight modular body structure and six 3-DOF legs. Each leg is actuated by three servos corresponding to hip, knee, and ankle motions. The curved leg structure increases obstacle-crossing capability while keeping the robot compact and lightweight.

<img src="/images/robot_platform.jpg" alt="Hexapod robot platform" style="width:100%; max-width:850px; border-radius:10px;">

Key design features include:

- Six-legged bionic locomotion platform
- Lightweight modular mechanical structure
- Curved leg design for improved obstacle traversal
- Adjustable body clearance for different terrain conditions
- Expandable sensing and control architecture

## Adaptive Gait and Clearance Control

A key feature of this robot is its ability to switch between different locomotion modes. In normal terrain, the robot uses a lower-clearance marching mode to reduce energy consumption. When encountering obstacles, it can increase its body clearance and switch to a step-over mode.

<img src="/images/motion.jpg" alt="Adaptive gait and foot trajectory" style="width:100%; max-width:850px; border-radius:10px;">

The adaptive gait strategy allows the robot to:

- Maintain stable tripod-like support during locomotion
- Adjust body clearance according to obstacle height
- Step over obstacles instead of always detouring around them
- Improve mobility in complex field environments
- Reduce unnecessary motion and energy consumption

## Sensing and Control System

The robot integrates sensing, control, and actuation modules for field-oriented locomotion. The posture sensing system provides robot attitude feedback, while the environmental sensing system can be extended with LiDAR, stereo cameras, and distance sensors for obstacle detection and navigation.

<img src="/images/connection.jpg" alt="Robot sensing and control system architecture" style="width:100%; max-width:850px; border-radius:10px;">

The system architecture includes:

- IMU-based posture sensing
- Force sensors for foot-ground contact detection
- Motion controller for servo-level actuation
- Optional LiDAR, stereo camera, and distance sensors for environmental perception
- Data processor for higher-level sensing and navigation functions

## Field Experiments

The robot was tested on different terrain conditions, including hard ground, grass, slopes, and complex field environments with obstacles. These experiments evaluated its stability, obstacle-crossing capability, and adaptability to agricultural field conditions.

<img src="/images/field_test.jpg" alt="Hexapod robot field test" style="width:100%; max-width:850px; border-radius:10px;">

The experiments demonstrated that the robot can maintain stable locomotion across uneven field environments and adjust its clearance when traversing obstacles. These results show the potential of bionic hexapod robots for field scouting and future precision agriculture applications.

## My Contributions

- Designed and built the bionic hexapod robot platform
- Developed the mechanical structure, leg configuration, and adjustable-clearance mechanism
- Integrated sensing, control, and actuation hardware for field deployment
- Implemented adaptive gait, clearance-control strategies, and robot simulation
- Collaborated with the team on field experiments and manuscript preparation

## Publication

Zhang Z, He W, Wu F, Quesada L and Xiang L (2024) Development of a bionic hexapod robot with adaptive gait and clearance for enhanced agricultural field scouting. Front. Robot. AI 11:1426269. doi: 10.3389/frobt.2024.1426269

[Paper](https://doi.org/10.3389/frobt.2024.1426269)
