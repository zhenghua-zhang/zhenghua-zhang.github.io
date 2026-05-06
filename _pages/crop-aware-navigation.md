---
title: "Crop-Aware Navigation for Adjustable-Clearance Hexapod Robots in Vine Crop Fields"
permalink: /projects/crop-aware-navigation/
author_profile: true
---

<img src="/images/crop_aware_navigation.jpg" alt="Crop-aware hexapod navigation" style="width:100%; max-width:850px; border-radius:10px;">

## Overview

This project develops a crop-aware navigation framework for an adjustable-clearance hexapod robot operating in cluttered vine crop fields. Vine crops such as cucurbits and sweetpotatoes form dense, low-lying vegetation structures that make conventional wheeled or tracked robots difficult to use without damaging plants.

To address this challenge, I developed a hierarchical navigation framework that integrates UAV-based aerial perception, semantic elevation mapping, energy-aware path planning, and local foothold refinement. Instead of treating all vegetation as rigid obstacles, the framework evaluates whether the robot should step over low vegetation or detour around dense obstacles, while updating individual footholds to reduce plant contact.

## System Overview

The system combines aerial perception with legged robot navigation. A UAV captures top-view RGB images of the field, which are processed using semantic segmentation and monocular depth estimation to construct a semantic elevation map. This map encodes both vegetation distribution and terrain height, providing the environmental representation required for crop-aware navigation.

<img src="/images/aghexanav_overview.jpg" alt="System overview of crop-aware navigation framework" style="width:100%; max-width:850px; border-radius:10px;">

The navigation framework consists of three main components:

- UAV-based semantic and elevation mapping
- Energy-aware global path planning with adaptive clearance
- Local foothold update for reducing vegetation contact

## Hexapod Robot Platform

The robot is designed with adjustable body clearance, allowing it to adapt its geometric configuration to different vegetation and obstacle heights. This capability is particularly useful in vine crop environments, where traversable regions are fragmented and vegetation height varies across the field.

<img src="/images/hexapod_platform.jpg" alt="Adjustable-clearance hexapod robot platform" style="width:100%; max-width:850px; border-radius:10px;">

Key platform features include:

- Six-legged support for enhanced stability
- Adjustable body clearance for stepping over low vegetation
- Large foothold search space for crop-safe locomotion
- Field-oriented sensing and computing architecture
- Compatibility with semantic mapping and path planning modules

## UAV-Based Semantic Elevation Mapping

The perception pipeline uses UAV imagery to build a global representation of the field. A semantic segmentation model classifies the scene into agricultural classes such as soil, vines, leaves, fruits, flowers, and obstacles. Monocular depth estimation is then used to recover terrain height and generate a 2.5D elevation map.

<img src="/images/semantic_elevation_map.jpg" alt="Semantic elevation mapping from UAV imagery" style="width:100%; max-width:850px; border-radius:10px;">

This semantic elevation map allows the planner to distinguish between:

- Soil regions that are safe for walking
- Low vegetation that may be stepped over
- Dense vegetation that should be avoided
- Rigid obstacles that require detours
- Candidate foothold regions for plant-safe locomotion

## Energy-Aware Path Planning

The global planner is formulated as an A*-based search over the robot state:

```text
s = [x, y, theta, h]
