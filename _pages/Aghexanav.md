---
title: "AgHexaNav: Contact-Aware Planning for Low-Damage Navigation of Legged Robots in Vine Crops"
permalink: /projects/Aghexanav/
author_profile: true
---

<img src="/images/Aghexanav.jpg" alt="Aghexanav" style="width:100%; max-width:850px; border-radius:10px;">

## Overview

After building the hexapod platform, the next question was how to get it to a target location in a real field. Conventional planners represent the robot as a body footprint and keep that footprint clear of obstacles. However, this assumption doesn't fits a legged robot in vine crops. Contact happens at discrete feet rather than continuously, and the region beneath the body does not need to be clear at all, since a vine can pass through the gap between the two rows of legs while the feet land on either side. Planning under the footprint assumption therefore produces detours that are not necessary and damage estimates that do not match what happens on the ground.

We therefore developed AgHexaNav, a contact-aware planning framework built on a dual-corridor contact model, which represents ground contact as the two strips where the feet actually land and treats body heading as a decision variable. On this model, two modules handle damage at different levels: a crop damage cost that steers the corridors away from fruit during path planning, and a foothold refinement that resolves the contacts a body path cannot foresee. Together they let the robot straddle a vine row where alignment allows and step over it where it does not, keeping fruit contact near zero without giving up path quality.

## Approach

We represent ground contact as two foothold corridors separated by a straddle gap, rather than a single body footprint. Because the corridors rotate with the robot, body heading becomes a decision variable, and its alignment with the vine direction determines whether the robot can straddle a row or must step over it. Two modules are built on this representation.

**Crop damage cost.** At the body level, a cost term steers the two corridors away from fruit, weighting fruit above foliage. It attaches to edge evaluation, so it works with A*, PRM, and Informed RRT* without modifying the planner itself.

**Foothold refinement.** At the leg level, each foot is adjusted within its reachable disk to leave any remaining contact, selected on reachability, stability, and minimal displacement, with a three tier fallback for the case where no admissible foothold exists.

<img src="/images/pipeline.png" alt="pipeline" style="width:100%; max-width:850px; border-radius:10px;">

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
