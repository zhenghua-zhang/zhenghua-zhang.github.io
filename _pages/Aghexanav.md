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

## ## Simulation experiments

Evaluated across four maps of varying vine and obstacle density and three planning paradigms, with and without each module.

<img src="/images/main_fig.png" alt="simulation" style="width:100%; max-width:850px; border-radius:10px;">

## Field Experiments

Validated on a cucumber field with the hexapod platform, using UAV-derived semantic elevation maps as planner input.

<img src="/images/RAL_new_07.png" alt="field" style="width:100%; max-width:850px; border-radius:10px;">

## My Contributions

- Formulated the dual-corridor contact model and introduced body heading as a decision variable
- Designed and implemented the crop damage cost module and its integration with A*, PRM, and Informed RRT*
- Developed the foothold refinement module with reachability, stability, and displacement criteria, and a three tier fallback
- Built the simulation framework and ran the full study across four maps and three planning paradigms
- Led the field experiments on the hexapod platform and prepared the manuscript as first author


[Paper](https://doi.org/10.3389/frobt.2024.1426269)
