---
layout: page
title: Raspberry Pi Autonomous Rover
permalink: /projects/raspi-autonomous-rover/
---

← [Back to Projects](/projects/)

**Platform:** Raspberry Pi  
**Domain:** Robotics · Autonomous Systems · Embedded Software  
**Type:** Self-driven engineering project  
**Status:** Work in progress

---

## Project Context

This project focuses on developing a **small-scale autonomous rover**
to explore the fundamentals of **vehicle autonomy, sensing, control, and embedded software**.

The rover is being built as a learning platform inspired by real-world
driver-assistance systems, implemented at a student-accessible scale using
a **Raspberry Pi**.

> **Work in Progress**  
> This project is under active development.  
> The current emphasis is on system architecture, algorithm validation,
> and understanding real-world constraints before expanding functionality.

---

## System Overview

The rover is designed as a **layered system**, integrating hardware,
perception, decision-making, and control.

At a high level, the system consists of:

- A Raspberry Pi acting as the main compute and control unit  
- Sensors for perception and state estimation  
- Actuators for steering and propulsion  
- Software modules for perception, planning, and control  

The focus is on **system integration and engineering understanding**,
not merely assembling hardware components.

---

## Autonomous Features Under Development

### Lane Keeping Assist (LKA)

An initial lane-keeping pipeline is being prototyped using a forward-facing camera
to estimate the rover’s lateral position relative to a lane.

Current focus areas include:

- Image acquisition and preprocessing  
- Lane feature extraction  
- Error estimation relative to a desired trajectory  
- Closed-loop steering correction  

This module introduces concepts of **computer vision**, **feedback control**,
and **real-time decision making**.

---

### Adaptive Cruise Control (ACC)

Adaptive Cruise Control functionality is being developed to regulate the rover’s
speed based on the distance to obstacles ahead.

Current focus areas include:

- Distance estimation using range sensors  
- Speed regulation logic based on a target following distance  
- Smooth acceleration and deceleration profiles  

This module emphasizes **longitudinal control** and safety-aware decision logic.

---

### Autonomous Emergency Braking (AEB)

An initial AEB mechanism is being explored to apply braking when a collision risk
is detected.

Current focus areas include:

- Threshold-based and time-to-collision logic  
- Priority override of throttle commands  
- Safety-oriented system behavior  

This module highlights **fail-safe design principles** in autonomous systems.

---

## Software Architecture

The rover software is structured into modular components:

- **Perception:** sensor data acquisition and preprocessing  
- **Decision Logic:** LKA, ACC, and AEB state machines  
- **Control:** steering and speed control  
- **Hardware Interface:** GPIO, motor drivers, and sensors  

This structure allows subsystems to be developed and tested independently.

---

## Control & Algorithms

Control strategies being explored include:

- Proportional and PID-based steering control  
- Speed control with acceleration limits  
- Priority arbitration between autonomy modules
  (e.g., AEB overriding ACC)

The emphasis is on understanding **control behavior and stability**,
not just implementation.

---

## Learning Outcomes (Ongoing)

Through this project, I am developing practical understanding of:

- Embedded programming on Raspberry Pi  
- Sensor integration and basic data fusion  
- Closed-loop control systems  
- Real-time constraints in robotic platforms  
- Safety considerations in autonomous behavior  

---

## Current Focus

The current phase of development focuses on:

- Improving robustness of lane detection under varying lighting conditions  
- Tuning control parameters for stable steering and speed control  
- Structuring the codebase for clarity and extensibility  
- Logging and debugging system behavior during real-world tests  

---

## Planned Extensions

Future work includes:

- Sensor fusion between camera and distance sensors  
- Improved trajectory planning logic  
- Simulation-based testing prior to deployment  
- Comparative evaluation of control strategies  
- Documentation of system behavior under edge cases  

---

## Credits & Acknowledgements

This is a self-driven project developed as part of my break-year focus on
robotics, autonomous systems, and embedded engineering.

← [Back to Projects](/projects/)
