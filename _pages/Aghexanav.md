---
title: "AgHexaNav: Contact-Aware Planning for Low-Damage Navigation of Legged Robots in Vine Crops"
permalink: /projects/Aghexanav/
author_profile: true
---

<meta name="robots" content="noindex, nofollow">

<style>
  #protected-content {
    display: none;
  }

  #password-screen {
    max-width: 430px;
    margin: 70px auto;
    padding: 30px;
    text-align: center;
    border: 1px solid #e1e4e8;
    border-radius: 10px;
    background: #f8f9fa;
  }

  #password-screen h2 {
    margin-top: 0;
    margin-bottom: 10px;
  }

  #password-screen p {
    color: #666;
    margin-bottom: 20px;
  }

  #password-input {
    width: 100%;
    box-sizing: border-box;
    padding: 11px 12px;
    margin-bottom: 12px;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 16px;
  }

  #password-button {
    width: 100%;
    padding: 11px 12px;
    border: none;
    border-radius: 6px;
    background: #4da3c7;
    color: white;
    font-size: 16px;
    cursor: pointer;
  }

  #password-button:hover {
    opacity: 0.9;
  }

  #password-error {
    color: #c62828 !important;
    margin-top: 12px;
    margin-bottom: 0 !important;
    display: none;
  }
</style>

<div id="password-screen">
  <h2>Protected Project</h2>
  <p>Please enter the password to view this project.</p>

  <input
    type="password"
    id="password-input"
    placeholder="Password"
    autocomplete="off"
  >

  <button id="password-button" onclick="checkPassword()">
    View Project
  </button>

  <p id="password-error">Incorrect password. Please try again.</p>
</div>

<div id="protected-content">

<img src="/images/Aghexanav.jpg" alt="Aghexanav" style="width:100%; max-width:850px; border-radius:10px;">

<div style="background-color:#f6f8fa; border-left:4px solid #4da3c7; padding:12px 16px; margin:18px 0; border-radius:6px; color:#444;">
  <strong>Note:</strong> Since this work is currently under review, only a high-level summary of the planning and foothold refinement framework is provided here. Detailed algorithmic implementation, quantitative results, and full experimental analysis will be added after publication.
</div>

## Overview

After building the hexapod platform, the next question was how to get it to a target location in a real field. Conventional planners represent the robot as a body footprint and keep that footprint clear of obstacles. However, this assumption doesn't fit a legged robot in vine crops. Contact happens at discrete feet rather than continuously, and the region beneath the body does not need to be clear at all, since a vine can pass through the gap between the two rows of legs while the feet land on either side. Planning under the footprint assumption therefore produces detours that are not necessary and damage estimates that do not match what happens on the ground.

We therefore developed AgHexaNav, a contact-aware planning framework built on a dual-corridor contact model, which represents ground contact as the two strips where the feet actually land and treats body heading as a decision variable. On this model, two modules handle damage at different levels: a crop damage cost that steers the corridors away from fruit during path planning, and a foothold refinement that resolves the contacts a body path cannot foresee. Together they let the robot straddle a vine row where alignment allows and step over it where it does not, keeping fruit contact near zero without giving up path quality.

## Approach

We represent ground contact as two foothold corridors separated by a straddle gap, rather than a single body footprint. Because the corridors rotate with the robot, body heading becomes a decision variable, and its alignment with the vine direction determines whether the robot can straddle a row or must step over it. Two modules are built on this representation.

**Crop damage cost.** At the body level, a cost term steers the two corridors away from fruit, weighting fruit above foliage. It attaches to edge evaluation, so it works with A*, PRM, and Informed RRT* without modifying the planner itself.

**Foothold refinement.** At the leg level, each foot is adjusted within its reachable disk to leave any remaining contact, selected on reachability, stability, and minimal displacement, with a three-tier fallback for the case where no admissible foothold exists.

<img src="/images/pipeline.png" alt="pipeline" style="width:100%; max-width:850px; border-radius:10px;">

## Simulation Experiments

Evaluated across four maps of varying vine and obstacle density and three planning paradigms, with and without each module.

<img src="/images/main_fig.png" alt="simulation" style="width:100%; max-width:850px; border-radius:10px;">

## Field Experiments

Validated on a cucumber field with the hexapod platform, using UAV-derived semantic elevation maps as planner input.

<img src="/images/RAL_new_07.png" alt="field" style="width:100%; max-width:850px; border-radius:10px;">

## My Contributions

- Formulated the dual-corridor contact model and introduced body heading as a decision variable
- Designed and implemented the crop damage cost module and its integration with A*, PRM, and Informed RRT*
- Developed the foothold refinement module with reachability, stability, and displacement criteria, and a three-tier fallback
- Built the simulation framework and ran the full study across four maps and three planning paradigms
- Led the field experiments on the hexapod platform and prepared the manuscript as first author

</div>

<script>
function checkPassword() {
  const password = document.getElementById("password-input").value;

  if (password === "201910") {
    document.getElementById("password-screen").style.display = "none";
    document.getElementById("protected-content").style.display = "block";

    sessionStorage.setItem("agHexaNavAccess", "granted");
  } else {
    document.getElementById("password-error").style.display = "block";
    document.getElementById("password-input").value = "";
    document.getElementById("password-input").focus();
  }
}

document.getElementById("password-input").addEventListener("keydown", function(event) {
  if (event.key === "Enter") {
    checkPassword();
  }
});

if (sessionStorage.getItem("agHexaNavAccess") === "granted") {
  document.getElementById("password-screen").style.display = "none";
  document.getElementById("protected-content").style.display = "block";
}
</script>
