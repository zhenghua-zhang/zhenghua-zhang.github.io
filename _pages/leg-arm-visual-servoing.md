---
title: "Heterogeneous Hexapod Robot with Leg-Arm Visual Servoing for Precision Field Manipulation"
permalink: /projects/leg-arm-visual-servoing/
author_profile: true
---

<img src="/images/leg_arm_visual_servoing.jpg" alt="Heterogeneous hexapod robot with leg-arm hybrid mechanism" style="width:100%; max-width:850px; border-radius:10px;">

## Overview

After developing hexapod robots for field navigation, the next challenge is enabling a legged robot to perform useful physical tasks after reaching a target location. In agricultural and field environments, this requires more than mobility: the robot must perceive a target, position an end-effector accurately, and interact with the environment while maintaining stable locomotion.

This ongoing project explores a heterogeneous hexapod robot with a 5-DOF leg-arm hybrid mechanism. The multifunctional limb can participate in normal walking and can also be reconfigured for precision manipulation tasks, such as targeted weed treatment. My current work focuses on mechanical design, gait reconstruction for the heterogeneous robot, and precision control of the leg-arm mechanism.

## Leg-Arm Hybrid Mechanism

The key idea is to convert one leg of the hexapod into a multifunctional limb. During locomotion, the limb contributes to the walking gait. During manipulation, it functions as a robotic arm equipped with a nozzle and a stereo camera for perception-guided targeting.

This design allows the robot to:

- Maintain stable locomotion with a heterogeneous limb configuration
- Use the 5-DOF limb for precise end-effector positioning
- Combine locomotion, perception, and manipulation in a single field robot
- Support local intervention tasks after navigation

## Stereo Vision and Target Localization

A stereo camera is mounted near the leg-arm end-effector to localize targets relative to the robot. In current experiments, AprilTags are used as synthetic weed targets to evaluate the visual targeting pipeline before deploying the system on real weed detection.

The perception pipeline uses stereo depth and image features to estimate the target location and provide visual feedback for end-effector aiming.

## Two-Stage Closed-Loop Aiming

A major challenge in this system is that precise calibration alone is not sufficient. The robot contains multiple servo joints, accumulated joint backlash, and hand-eye calibration errors. Instead of relying entirely on perfect extrinsic calibration, I developed a two-stage aiming strategy.

The first stage uses 5-DOF inverse kinematics for coarse positioning. The second stage applies image-based visual servoing to reduce the remaining image-plane error. This structure allows the system to tolerate mechanical imprecision and refine the final aim through visual feedback.

<img src="/images/ibvs_convergence.jpg" alt="Closed-loop visual servoing convergence" style="width:100%; max-width:850px; border-radius:10px;">

## Depth-Conditioned Reticle Calibration

To handle depth-dependent aiming offsets, I measured where the spray actually lands in the camera frame at different working distances. Instead of treating calibration as a fixed geometric transform, the system uses a depth-conditioned lookup table that maps working distance to the expected aim point in the image.

<img src="/images/reticle_calibration.jpg" alt="Depth-conditioned reticle calibration" style="width:100%; max-width:850px; border-radius:10px;">

This approach is designed to make the system robust to small mechanical shifts, calibration residuals, and joint backlash.

## Technical Highlights

- Heterogeneous hexapod robot with a 5-DOF leg-arm hybrid mechanism
- Gait reconstruction for asymmetric legged locomotion
- Stereo vision-based target localization
- Two-stage aiming: 5-DOF inverse kinematics followed by 2-DOF image-based visual servoing
- Depth-conditioned reticle lookup for hardware-aware targeting
- Closed-loop correction designed to tolerate calibration error and servo backlash

## My Contributions

- Designed the 5-DOF leg-arm hybrid mechanism for the heterogeneous hexapod robot
- Developed mechanical integration between the multifunctional limb, nozzle, and stereo camera
- Reconstructed the gait strategy for a hexapod robot with asymmetric limb functions
- Developed kinematic modeling and precision control methods for the leg-arm mechanism
- Implemented the two-stage visual servoing pipeline for perception-guided targeting
- Built and tested the hardware system for precision field manipulation

## Status

This project is currently in progress. I am working on mechanical refinement, heterogeneous gait reconstruction, stereo vision integration, and closed-loop precision control of the leg-arm mechanism.
