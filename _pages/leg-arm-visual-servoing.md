---
title: "Heterogeneous Hexapod Robot with a 5-DOF Leg-Arm Hybrid Limb"
permalink: /projects/leg-arm-visual-servoing/
author_profile: true
---

<img src="/images/leg_arm_visual_servoing.jpg" alt="Heterogeneous hexapod robot with leg-arm hybrid mechanism" style="width:100%; max-width:850px; border-radius:10px;">

<div style="background-color:#f6f8fa; border-left:4px solid #4da3c7; padding:12px 16px; margin:18px 0; border-radius:6px; color:#444;">
  <strong>Note:</strong> This project is ongoing. The page provides a high-level summary of the system design and control strategy; additional experimental results will be added after validation is complete.
</div>

## Overview

After developing hexapod robots for field navigation, the next challenge is enabling a legged robot to perform useful physical tasks after reaching a target location. In field environments, this requires more than mobility: the robot must perceive a target, position an end-effector accurately, and interact with the environment while maintaining stable locomotion.

This ongoing project explores a heterogeneous hexapod robot with a 5×4-DOF + 1×5-DOF limb configuration. The robot retains five standard 4-DOF locomotion legs, while one limb is redesigned as a 5-DOF leg-arm hybrid limb. During walking, the hybrid limb functions as a locomotion leg; during task execution, it transitions into a manipulation mode for perception-guided nozzle positioning and targeted spraying.

## Leg-Arm Hybrid Limb Design

The key idea is to redesign one leg of the hexapod as a 5-DOF leg-arm hybrid limb. During locomotion, the hybrid limb participates in the walking gait as a support leg. During task execution, it is reconfigured for precision manipulation, allowing the robot to aim a nozzle at nearby weed targets.

A stereo camera is mounted near the hybrid limb end-effector to localize targets relative to the robot. In the current stage, visual markers are used as synthetic weed targets to evaluate the perception-guided targeting pipeline before deployment with real weed detection.

<img src="/images/heterogeneous_hexapod_design.jpg" alt="Design of the heterogeneous hexapod robot and 5-DOF leg-arm hybrid limb" style="width:100%; max-width:850px; border-radius:10px;">

This design allows the robot to:

- Maintain legged locomotion with a heterogeneous limb configuration
- Use the hybrid limb for precise end-effector positioning
- Integrate stereo sensing near the end-effector for target localization
- Combine locomotion, perception, and manipulation in a single field robot
- Perform local intervention tasks after navigation

## Depth-Conditioned Reticle Calibration

To handle depth-dependent aiming offsets, I measured where the spray actually lands in the camera frame at different working distances. Instead of treating calibration as a fixed geometric transform, the system uses a depth-conditioned lookup table that maps working distance to the expected aim point in the image.

<img src="/images/reticle_calibration.jpg" alt="Depth-conditioned reticle calibration" style="width:100%; max-width:850px; border-radius:10px;">

This approach is designed to make the system robust to small mechanical shifts, calibration residuals, and joint backlash.

## Two-Stage Closed-Loop Aiming

A major challenge in this system is that precise calibration alone is not sufficient. The robot contains multiple servo joints, accumulated joint backlash, and hand-eye calibration residuals. Instead of relying entirely on perfect extrinsic calibration, I developed a two-stage aiming strategy that combines model-based positioning with visual feedback.

In the first stage, a 5-DOF inverse kinematics solver moves the hybrid limb to a coarse aiming pose. In the second stage, image-based visual servoing is used to reduce the remaining image-plane error. This structure allows the system to tolerate mechanical imprecision and refine the final aim through closed-loop correction.

<img src="/images/ibvs_convergence.jpg" alt="Closed-loop visual servoing convergence" style="width:100%; max-width:850px; border-radius:10px;">

## Technical Highlights

- Heterogeneous hexapod robot with a 5-DOF leg-arm hybrid mechanism
- Gait reconstruction for asymmetric legged locomotion
- Stereo vision-based target localization
- Two-stage aiming: 5-DOF inverse kinematics followed by 2-DOF image-based visual servoing
- Depth-conditioned reticle lookup for hardware-aware targeting
- Closed-loop correction designed to tolerate calibration error and servo backlash

## My Contributions

- Led the 5-DOF leg-arm hybrid limb design and mentored an undergraduate student in mechanical design and prototyping
- Developed the mechanical integration between the hybrid limb, nozzle, and stereo camera
- Reconstructed the gait strategy for a heterogeneous hexapod with asymmetric limb functions
- Developed kinematic modeling and precision control methods for the leg-arm hybrid limb
- Implemented the two-stage visual servoing pipeline for perception-guided targeting
- Built the hardware system and am currently conducting experimental validation for precision field manipulation

## Status

This project is currently in progress. I am working on mechanical refinement, heterogeneous gait reconstruction, stereo vision integration, and closed-loop precision control of the leg-arm mechanism.
