---
title: "Design and Evaluation of a Leg-Manipulator for Ultra-Precision Spot Spraying of Weed Seedlings"
permalink: /projects/leg-manipulator/
author_profile: true
published: true
---

<img src="/images/system_overview1.png" alt="Heterogeneous hexapod robot with a 5-DOF leg-arm hybrid limb" style="width:100%; max-width:850px; border-radius:10px;">

## Overview

After building hexapod robots that can navigate a field, the next question was what the robot does once it arrives. Weed control works best at the seedling stage, aimed at the growing point of each weed, which means placing a microliter dose within a few millimeters of a target that is small, low to the ground, and often partly hidden. Existing weeding sprayers do not reach this scale in the field.

The usual way to give a legged robot manipulation is to mount an arm on its back, which costs payload and raises the center of mass, the opposite of what is needed for inspecting seedlings near the soil. We instead reconfigured one of the six walking legs into the sprayer itself, a composite limb that walks with the other legs and switches to a precision spraying mode when a weed is detected. The harder problem turned out to be aiming rather than mechanism: a liquid jet is beyond control once it leaves the nozzle, so conventional hand-eye calibration does not apply, and the landing point is shifted by gravity, drag, backlash, and wind.

<div style="background-color:#f6f8fa; border-left:4px solid #4da3c7; padding:12px 16px; margin:18px 0; border-radius:6px; color:#444;">
  <strong>Note:</strong> This project is ongoing. This page provides only a high-level summary of the system concept and hardware design. Additional technical details will be added after the work is published.
</div>

## Leg-manipulator design

Spraying needs control of nozzle position plus pitch and yaw, so five degrees of freedom is the minimum without redundancy. The limb replaces the original 4-DOF walking leg with a hip-yaw joint, a hip-pitch joint, a knee-pitch joint, and a two-axis wrist.

The foot doubles as the end effector. A solenoid valve and nozzle sit coaxially inside the support tube behind two spring-loaded caps, which stay shut during walking to shield the nozzle from soil and open when a linear solenoid pushes the valve forward to spray. A stereo camera sits behind and above the nozzle with its optical axis parallel to the spray direction.

<img src="/images/leg_nozzle.png" alt="Design of the heterogeneous hexapod robot, hybrid limb, nozzle, and stereo camera" style="width:100%; max-width:850px; border-radius:10px;">

## Two-stage targeting

**Ballistic inverse kinematics** provides the coarse aim, solving for a joint configuration whose spray ray passes through the target. Aiming constrains only two of five degrees of freedom, so the redundancy is resolved with a stand-off barrier and a warm start from the observation pose.

**Aim-point lookup and visual servoing** close the loop. At a given depth the jet strikes a fixed pixel regardless of joint configuration, so the ballistic bias is absorbed by a depth-conditioned lookup rather than modeled. Image-Based Visual Servoing (IBVS) then drives the target onto that pixel, actuating only two joints, since moving the proximal ones would displace the camera itself.

## Experiments

Indoors, the two stages reduced the image error by well over an order of magnitude, with the dispensed points scattering around the target without systematic offset, confirming the lookup removes the ballistic bias rather than redirecting it.

<img src="/images/fig_indoor.png" alt="indoor_test" style="width:100%; max-width:850px; border-radius:10px;">

In the field, the robot walked to a standing position near each target and ran the same pipeline on natural vegetation under uncontrolled light and wind, reaching the intended target in every trial at millimeter scale.

<img src="/images/grass.jpg" alt="field_test" style="width:100%; max-width:850px; border-radius:10px;">

## My Contributions

- Designed the 5-DOF leg-manipulator and its foot module, and mentored an undergraduate student on mechanical design and prototyping
- Formulated the ballistic inverse kinematics and implemented the solver
- Developed the depth-conditioned aim-point lookup and the visual servoing controller
- Built the Hexa-Weeder platform, including the spraying system, onboard computing, and stereo sensing
- Ran the indoor validation and field trials
