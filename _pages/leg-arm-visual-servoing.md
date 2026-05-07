---
title: "Heterogeneous Hexapod Robot with a 5-DOF Leg-Arm Hybrid Limb"
permalink: /projects/leg-arm-visual-servoing/
author_profile: true
published: false
---

<img src="/images/leg_arm2.jpg" alt="Heterogeneous hexapod robot with a 5-DOF leg-arm hybrid limb" style="width:100%; max-width:850px; border-radius:10px;">

## Overview

After developing hexapod robots for field navigation, the next challenge is enabling a legged robot to perform useful physical tasks after reaching a target location. In field environments, this requires more than mobility: the robot must perceive a target, position an end-effector, and interact with the environment while maintaining stable locomotion.

This ongoing project explores a heterogeneous hexapod robot with a 5×4-DOF + 1×5-DOF limb configuration. The robot retains five standard 4-DOF locomotion legs, while one limb is redesigned as a 5-DOF leg-arm hybrid limb. During walking, the hybrid limb functions as a locomotion leg; during task execution, it transitions into a manipulation mode for perception-guided field intervention.

<div style="background-color:#f6f8fa; border-left:4px solid #4da3c7; padding:12px 16px; margin:18px 0; border-radius:6px; color:#444;">
  <strong>Note:</strong> This project is ongoing. This page provides only a high-level summary of the system concept and hardware design. Additional technical details will be added after the work is published.
</div>

## Leg-Arm Hybrid Limb Design and Stereo Sensing

The key idea is to redesign one leg of the hexapod as a 5-DOF leg-arm hybrid limb. During locomotion, the hybrid limb participates in the walking gait as a support leg. During task execution, it is reconfigured for precision manipulation, allowing the robot to perform localized field operations.

A stereo camera is mounted near the hybrid limb end-effector to support target localization and perception-guided manipulation.

<img src="/images/heterogeneous_hexapod_design.jpg" alt="Design of the heterogeneous hexapod robot, hybrid limb, nozzle, and stereo camera" style="width:100%; max-width:850px; border-radius:10px;">

This design allows the robot to:

- Maintain legged locomotion with a heterogeneous limb configuration
- Use the hybrid limb for localized manipulation tasks
- Integrate stereo sensing near the end-effector
- Combine locomotion, perception, and manipulation in a single field robot

## Heterogeneous Gait Reconstruction

Replacing one standard leg with a 5-DOF leg-arm hybrid limb changes the robot morphology and requires gait reconstruction. The robot must maintain stable locomotion even when one limb has different kinematic properties and may switch between support and manipulation roles.

My current work focuses on reconstructing the gait strategy for this asymmetric configuration, including support redistribution, stable locomotion with a heterogeneous limb, and coordination between locomotion and task-execution phases.

## Technical Highlights

- Heterogeneous hexapod robot with a 5-DOF leg-arm hybrid limb
- Locomotion-manipulation integration for field robotics
- Gait reconstruction for asymmetric legged locomotion
- Stereo sensing for perception-guided field intervention
- Mechanical integration of a multifunctional limb, nozzle, and camera system

## My Contributions

- Led the 5-DOF leg-arm hybrid limb design and mentored an undergraduate student in mechanical design and prototyping
- Developed the mechanical integration between the hybrid limb, nozzle, and stereo camera
- Reconstructed the gait strategy for a heterogeneous hexapod with asymmetric limb functions
- Developed kinematic modeling and precision control methods for the leg-arm hybrid limb
- Built the hardware system and am currently conducting experimental validation

## Status

This project is currently in progress. I am working on mechanical refinement, heterogeneous gait reconstruction, stereo sensing integration, and experimental validation of the leg-arm hybrid system.
