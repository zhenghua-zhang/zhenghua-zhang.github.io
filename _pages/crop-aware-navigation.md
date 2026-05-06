---
title: "Crop-Aware Navigation for Adjustable-Clearance Hexapod Robots in Vine Crop Fields"
permalink: /projects/crop-aware-navigation/
author_profile: true
---

<img src="/images/crop_aware_navigation.jpg" alt="Crop-aware hexapod navigation in vine crop field" style="width:100%; max-width:850px; border-radius:10px;">

## Overview

This project develops a crop-aware navigation framework for an adjustable-clearance hexapod robot operating in cluttered vine crop fields. Vine crops such as cucurbits and sweetpotatoes form dense, low-lying vegetation structures, where conventional wheeled or tracked platforms may cause unintended plant damage.

The goal of this project is to enable a legged robot to navigate through dense agricultural environments by combining aerial perception, semantic mapping, adaptive-clearance planning, and foothold-level motion refinement. Instead of treating all vegetation as rigid obstacles, the framework uses crop-aware environmental information to support safer navigation decisions.

## System Overview

The system integrates UAV-based aerial perception with hexapod robot navigation. A UAV captures top-view RGB images of the field, which are processed to extract semantic and geometric information. The resulting map representation provides the planner with both vegetation distribution and terrain structure.

<img src="/images/aghexanav_overview.jpg" alt="System overview of crop-aware navigation framework" style="width:100%; max-width:850px; border-radius:10px;">

The navigation framework includes:

- UAV-based field imaging
- Scene understanding using semantic segmentation and depth estimation
- Semantic elevation map construction
- Global path planning with adaptive clearance
- Foothold refinement for reducing plant contact
- Hexapod navigation in cluttered vine-crop environments

## Adjustable-Clearance Hexapod Platform

The robot is designed with adjustable body clearance, allowing it to adapt its geometric configuration to different vegetation and obstacle heights. This capability is particularly useful in vine crop environments, where vegetation fragments the traversable space and creates constraints for both body motion and foot placement.

<img src="/images/hexapod_platform.jpg" alt="Adjustable-clearance hexapod robot platform" style="width:100%; max-width:850px; border-radius:10px;">

Key platform features include:

- Six-legged support for enhanced stability
- Adjustable body clearance for traversing low vegetation
- Large foothold search space for crop-aware locomotion
- Modular sensing, computing, and actuation architecture
- Compatibility with aerial mapping and planning modules

## Semantic Field Understanding

The perception pipeline uses UAV imagery to build a field-level representation for navigation. Semantic segmentation is used to identify agricultural elements such as vines, leaves, fruits, flowers, and obstacles. This semantic information is combined with elevation estimation to support crop-aware planning.

<img src="/images/semantic_elevation_map.jpg" alt="Semantic segmentation results for vine crop field" style="width:100%; max-width:850px; border-radius:10px;">

This representation helps the robot distinguish between:

- Traversable soil regions
- Low vegetation that may be stepped over
- Dense vegetation that should be avoided
- Rigid obstacles requiring detours
- Candidate foothold regions for safer locomotion

## Crop-Aware Planning and Foothold Refinement

The navigation framework is designed to exploit the mobility advantages of legged robots. The global planner considers the robot position, heading, and body clearance, allowing the robot to adapt its morphology during navigation. This enables the robot to reason about when to raise its body, when to step over low vegetation, and when to detour around dense obstacles.

At the local level, nominal footholds are refined when they overlap with vegetation or obstacles. Candidate footholds are evaluated based on reachability, stability, and deviation from the nominal gait pattern. This allows the robot to reduce unnecessary plant interaction while maintaining stable locomotion.

<div style="background-color:#f6f8fa; border-left:4px solid #4da3c7; padding:12px 16px; margin:18px 0; border-radius:6px; color:#444;">
  <strong>Note:</strong> Since this work is currently under review, only a high-level summary of the planning and foothold refinement framework is provided here. Detailed algorithmic implementation, quantitative results, and full experimental analysis will be added after publication.
</div>

## Technical Highlights

- Crop-aware navigation for cluttered vine-crop environments
- UAV-based semantic and elevation mapping
- Adjustable-clearance hexapod locomotion
- Energy-aware global path planning
- Local foothold refinement for reducing plant contact
- Greenhouse validation under different vegetation densities

## My Contributions

- Designed and integrated the adjustable-clearance hexapod robot system
- Developed the crop-aware navigation framework
- Built the UAV-based semantic mapping pipeline
- Implemented adaptive-clearance global path planning
- Developed the local foothold refinement strategy
- Conducted greenhouse navigation experiments
- Prepared manuscript figures, analysis, and writing materials

## Manuscript

Z. Zhang, P. Xie, F. Wu, W. He, S. Du, and L. Xiang,  
“Crop-Aware Navigation for Adjustable-Clearance Hexapod Robots in Vine Crop Fields,”  
manuscript under review.
