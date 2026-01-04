---
layout: page
title: Projects
permalink: /projects/
---

### 1. Concept Car Aerodynamics: Geometry Development and CFD Pipeline

**Domain:** Automotive Design and Aerodynamics  
**Tools:** Blender, snappyHexMesh, OpenFOAM, ParaView  
**Status:** Core pipeline implemented and validated

A self-driven follow-up project extending my **IED Turin car design work** into a complete  
**design–simulation–physical prototyping pipeline**, built entirely using open-source tools.

The project focuses on taking an early-stage concept car design through
**geometry refinement, meshing, solver setup, convergence, and validation**, with emphasis on
engineering-aware modeling, numerical stability, and iterative refinement rather than visual styling alone.

**Focus areas**

- Surface continuity and mesh-aware modeling in Blender  
- Preparation of CFD-suitable, watertight external geometry  
- Unstructured hex-dominant meshing using snappyHexMesh  
- Steady-state external aerodynamics using OpenFOAM (simpleFoam)  
- Flow visualization and qualitative interpretation in ParaView  
- Physical prototyping through 3D printing and feedback-driven geometry iteration  

[Read the full CFD project write-up →](/projects/cfd-car-geometry/)

---

### 2. IED Turin – Automotive Concept Design (Onsite Summer Program)

This project forms the **design foundation** for my later work in computational aerodynamics,
geometry refinement, and physical prototyping.

In summer 2025, I attended a **three-week onsite automotive design program** at  
**Istituto Europeo di Design (IED), Turin**.

The course focused on the complete exterior car design workflow, from sketching and proportion
studies to physical model development.

**Course highlights**

- Studio sessions on proportions, stance, and surface language  
- Iterative sketching with one-to-one faculty feedback  
- Translating concepts into a physical clay model  
- Classroom sessions on automotive design trends  

**My work during the course**

- Developed an original exterior concept for a compact performance car  
- Created side, front, and rear views exploring surface treatments  
- Built a digital version of the selected concept for refinement  
- Constructed a physical clay model using the course workflow  
- Presented the final design to faculty and peers  

**Industry Exposure (Garage Visits)**

Alongside studio coursework, I visited several specialist automotive garages
in and around Turin, gaining exposure to fabrication techniques, performance
vehicle restoration, and motorsport-influenced modification processes.

These visits helped connect **design intent** with **real-world build constraints**.

[View full IED Turin project with photos →](/projects/ied-turin/)

---

### 3. ADAS Simulation and Deployment Platform using Raspberry Pi (In Progress)

An engineering-focused robotics project aimed at building a **modular simulation and deployment
platform** for **Advanced Driver Assistance Systems (ADAS)** concepts.

Rather than starting with a fully autonomous rover, this project follows an
**infrastructure-first approach**, where ADAS algorithms are:

- developed and validated on a laptop using simulation and replayable data,
- tested through clean hardware-agnostic interfaces, and
- incrementally deployed onto a Raspberry Pi–based rover only after verification.

Initial simulation dashboards for **AEB and ACC scenarios are functional** and used for
behavior verification across controlled test cases.

**ADAS capabilities under active development**

- Lane Keeping Assist (LKA)  
- Adaptive Cruise Control (ACC)  
- Autonomous Emergency Braking (AEB)  

**Core focus areas**

- Hardware abstraction and mock sensor interfaces  
- Laptop-based simulation and algorithm validation  
- Real-time sensing and control on Raspberry Pi  
- Controlled transition from simulation to hardware execution  
- Embedded software structure, safety constraints, and observability  

This project serves as a **testbed for embedded systems, robotics, and ADAS-oriented system design**,
with features introduced only after validation in a controlled environment.

[View ADAS simulation platform architecture and scenarios →](/projects/adas-rover/)

---

This portfolio highlights a **deliberately curated set of projects** that reflect
my interests in mechanical engineering, aerodynamics, and autonomous systems,
with emphasis on depth, correctness, and iterative engineering practice.
