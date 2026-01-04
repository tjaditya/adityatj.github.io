---
layout: page
title: ADAS Simulation and Deployment Platform using Raspberry Pi
permalink: /projects/adas-rover/
---

[Back to Projects](/projects/)

**Tools:** Raspberry Pi, Python, C++, Sensor Interfaces, Control Logic  
**Domain:** Robotics, Embedded Systems, ADAS  
**Type:** Infrastructure-first, systems-engineering project  
**Status:** Active development — working simulation environment with ACC/AEB scenarios

**GitHub Repository:**  
👉 [https://github.com/tjaditya/adas-simulation-platform](https://github.com/tjaditya/adas-simulation-platform)

*A working laptop-based simulation environment currently supports scenario-driven execution of ACC and AEB logic with full state observability.*

---

## Project Context

Advanced Driver Assistance Systems (ADAS) are **safety-critical, real-time systems** that cannot be developed reliably through direct trial-and-error on physical hardware. In professional automotive and robotics workflows, control and perception algorithms are first **designed, simulated, validated, and stress-tested** before being deployed to embedded platforms.

This project is therefore **not an attempt to rapidly build an autonomous rover**, but a deliberate effort to design a **development and deployment infrastructure** that reflects real-world ADAS engineering practice.

The rover serves as a **controlled execution platform**, while the primary focus of the project is on **system architecture, validation workflows, and observable system behavior**, rather than feature breadth.

---

## Project Objective

The objective of this project is to build a **modular ADAS experimentation platform** that enables:

- laptop-based simulation and algorithm development  
- deterministic validation using mock and replayable sensor inputs  
- strict separation between algorithms and hardware  
- controlled, incremental deployment to embedded systems  
- systematic observation, logging, and debugging of system behavior  

---

## Simulation Capabilities (Current Implementation)

A functional version of the platform is operational in the **laptop-based simulation environment**, enabling controlled execution of selected ADAS behaviors under predefined scenarios.

The simulation framework allows individual ADAS capabilities to be **explicitly enabled or disabled**, and system behavior to be observed deterministically using mocked and replayable sensor inputs.

Currently supported in simulation:

- **Adaptive Cruise Control (ACC):** longitudinal distance and speed regulation relative to a simulated lead object  
- **Autonomous Emergency Braking (AEB):** collision risk evaluation and braking intervention under critical conditions  

Simulation runs expose **distance profiles, feature state transitions, timing effects, and priority overrides**, enabling repeatable analysis of control decisions and feature interaction without exposing physical hardware to risk.

The simulation environment is intended strictly as a **development and validation tool**. Observed behaviors are scenario-specific and do not imply real-world robustness or safety certification. All capabilities must demonstrate stable and predictable behavior in simulation before any constrained hardware deployment is considered.

### Edge-Case Scenario: Sudden Cut-In

The platform is used to examine system behavior under **transient, safety-critical conditions** where rapid changes in the environment require interaction between multiple ADAS features.

![ADAS simulation – sudden cut-in scenario with ACC and AEB](/assets/projects/adas/sudden-cut-in.png)

*Simulation run showing distance-to-lead-object over time (top) and internal ACC/AEB state timelines (bottom) during a sudden cut-in scenario.*

In this scenario:
- a rapid reduction in lead-object distance is introduced through the scenario definition  
- **ACC transitions from cruise to slowdown** as longitudinal control responds  
- **AEB arms and triggers intermittently** when collision-risk thresholds are crossed  
- priority handling ensures that **emergency braking behavior overrides ACC** during critical intervals  

The emphasis here is on **behavioral clarity, timing, and traceability**, not on claiming real-world robustness.

---

## System-Level Overview

The platform is organized around **two tightly coupled execution environments** that share identical logical interfaces.

### Laptop-Based Development and Simulation Environment

The laptop environment is used for:

- development of perception and control algorithms  
- simulation and replay of sensor data streams  
- visualization, debugging, and behavioral analysis  
- validation of control logic without hardware risk  

All algorithms are written against **hardware-agnostic interfaces**, allowing identical code paths to be exercised in both simulation and embedded execution.

### Embedded Execution Environment (Raspberry Pi)

The Raspberry Pi–based rover is responsible for:

- acquisition of real sensor data  
- real-time control loop execution  
- actuator control (motors and braking)  
- enforcement of timing, safety, and priority constraints  

The embedded system implements the **same logical interfaces** used in simulation, enabling validated algorithms to transition from laptop to hardware with minimal modification.

---

## System Architecture

The diagram below illustrates the end-to-end architecture of the ADAS simulation and deployment platform, highlighting the separation between **algorithm development**, **validation**, and **embedded execution**.

![ADAS system architecture diagram](/assets/projects/adas/architecture.png)

*System architecture showing laptop-based simulation, hardware abstraction, and Raspberry Pi embedded execution.*

---

## Runtime Observability

The platform includes **development-time observability tooling** to inspect live telemetry, internal ADAS states, and feature interactions during simulation runs. This supports traceability of decisions, timing behavior, and priority handling under both steady-state and edge-case scenarios.

---

## Development Philosophy

This project follows an **infrastructure-first, safety-aware development philosophy** inspired by professional ADAS workflows.

Key principles include:

- **Hardware Abstraction Layer (HAL):** Sensors and actuators are accessed exclusively through abstract interfaces, isolating algorithms from hardware-specific details  
- **Mock and Replay-Based Testing:** Sensor behavior can be simulated or replayed from recorded data to enable deterministic, repeatable testing  
- **Validation Before Deployment:** Algorithms must demonstrate stable and predictable behavior in simulation before interacting with physical hardware  
- **Incremental Capability Enablement:** Only one ADAS capability is introduced at a time to control system complexity and reduce risk  

---

## Target ADAS Capabilities (Planned)

### Lane Keeping Assist (LKA) *(architecture defined; implementation pending)*
- Lane detection and estimation  
- Steering correction logic  
- Stability under varying inputs  

### Adaptive Cruise Control (ACC)
- Distance and relative speed estimation  
- Longitudinal speed control  
- Smooth response to changing lead-object behavior  

### Autonomous Emergency Braking (AEB)
- Collision risk estimation  
- Decision thresholds and braking logic  
- Highest-priority override behavior  

---

## Incremental Development Stages

### Stage 1 – Platform Bring-Up *(In Progress)*
- Raspberry Pi setup and remote access  
- Validation of GPIO, motor drivers, and basic actuation  
- Initial sensor communication tests  

### Stage 2 – Simulation and Replay Pipeline *(Complete for ACC/AEB)*
- Mock sensor interfaces for laptop execution  
- Recorded data playback for repeatable validation  
- Algorithm verification independent of hardware  

### Stage 3 – Single-Feature Deployment
- Deployment of one ADAS capability at a time  
- Low-speed, constrained hardware testing  
- Logging and behavioral verification  

### Stage 4 – Multi-Feature Integration
- Priority handling (e.g., AEB overriding ACC)  
- Interaction between perception and control layers  
- System-level testing and refinement  

---

## Tooling and Technology Choices

- Raspberry Pi as the embedded execution platform  
- Python and C++ for algorithm and control logic  
- Distance and vision sensors *(planned)*  
- Simulation, replay, and scenario tooling for validation  
- Data logging and visualization tools  

Technology choices favor **transparency, debuggability, and iteration speed** over performance optimization.

---

## Development Notes

AI-assisted coding tools were used selectively for **visualization and UI scaffolding**. All system architecture, control logic, state handling, and scenario definitions were designed and reviewed manually, with AI output treated as a productivity aid rather than an author.

---

## Engineering Value and Learning Outcomes

This project demonstrates:

- systems-level thinking in robotics and ADAS  
- safety-aware, validation-driven development practices  
- disciplined separation between software logic and hardware execution  
- controlled, incremental integration of complex features  
- understanding of how real-world ADAS systems are engineered and validated  

---

[Back to Projects](/projects/)
