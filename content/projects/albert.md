---
title: "ALBERT"
description: "LQR-guided rocket flight computer — custom PCB, dual STM32, Extended Kalman Filter, and full state-feedback fin control."
date: 2025-09-01
category: "Diploma Thesis"
year: "2025"
accent: "#c45d3e"
tags: ["STM32", "LQR", "Embedded C", "PCB Design", "MATLAB", "Kalman Filter"]
cover: ""
gallery:
  - src: "/images/projects/albert-pcb.jpg"
    alt: "ALBERT PCB top view"
    caption: "Custom dual-chip STM32 flight computer — 4-layer PCB"
  - src: "/images/projects/albert-assembly.jpg"
    alt: "Rocket assembly"
    caption: "Final assembly with fin actuators"
  - src: "/images/projects/albert-sim.jpg"
    alt: "MATLAB simulation"
    caption: "6-DOF trajectory simulation in MATLAB"
links:
  - label: "GitHub"
    url: "https://github.com/felixznr"
weight: 1
---

## Overview

ALBERT is a custom flight computer for a fin-controlled model rocket, designed and built as my diploma thesis at HTBLUVA Salzburg. The system uses full state-feedback control (LQR) to actively stabilize the rocket during powered flight.

## The Problem

Model rockets are inherently unstable — especially when you start adding active fin control. You need a system that can estimate the rocket's state in real time (attitude, angular rates, velocity) and compute control inputs fast enough to keep everything pointed the right direction.

## Approach

The flight computer is a dual-chip STM32 design. One processor handles sensor acquisition and state estimation via an Extended Kalman Filter, while the second handles the control loop and fin actuation. LQR gains are synthesised offline in MATLAB using a linearised 6-DOF model, then deployed as fixed-point constants on the microcontroller.

The full stack includes:

- **Hardware:** Custom 4-layer PCB with IMU, barometer, GPS, and four servo drivers
- **Firmware:** Bare-metal C with a cooperative scheduler, running the EKF at 200 Hz and the control loop at 100 Hz
- **Simulation:** Full 6-DOF MATLAB/Simulink model for gain tuning and trajectory prediction

## What I learned

This project taught me that the hardest part of control systems isn't the math — it's making real hardware behave like your model assumes it does. Sensor noise, actuator dynamics, and thermal drift all conspire to make the gap between simulation and reality very real.
