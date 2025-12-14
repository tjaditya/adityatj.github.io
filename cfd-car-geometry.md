---
layout: page
title: Concept Car Body Design & CFD-Ready Geometry Development
permalink: /projects/cfd-car-geometry/
---
← [Back to Projects](/projects/)

**Tools:** Blender · cfMesh · OpenFOAM · ParaView  
**Domain:** Automotive Design & Aerodynamics  
**Type:** Self-driven follow-up project  
**Status:** In progress

---

## Project Context

This project is a follow-up to a **3-week onsite summer course in _Introduction to Car Design_** at  
**Istituto Europeo di Design (IED), Turin**.

The objective was to take an early-stage concept design and develop it into a  
**CFD-ready 3D geometry**, suitable for airflow analysis using a fully open-source CFD pipeline.

The focus of this work extends beyond visual form to **engineering-aware surface development**,  
ensuring the geometry can be meshed and simulated reliably.

---

## Concept & Early Form Exploration

The initial phase focused on exploring overall proportions, stance, and surface flow using Blender.

Attention was given to:

- Wheel arch placement  
- Frontal intake shaping  
- Roof curvature and rear taper  

These decisions were made to establish an aerodynamic intent at the concept stage.

At this phase, the emphasis was on **form exploration**, without prematurely constraining the design
based on simulation requirements.

---

## Full Body Surface Development

The concept was progressively refined into a continuous full-body shell.

Key refinements included:

- Smoothing abrupt curvature transitions  
- Improving surface continuity across major panels  
- Eliminating visually appealing but non-physical sharp edges  

These changes were made with the understanding that  
**surface quality directly impacts CFD mesh stability and solution accuracy**.

---

## Topology & Mesh-Aware Modeling

Once the overall form was established, the model was reworked with **mesh awareness** in mind.

Steps taken:

- Clean and consistent topology aligned with surface curvature  
- Removal of non-manifold edges  
- Reduction of unnecessary geometric complexity  
- Preparation for watertight surface export  

This phase was critical in bridging the gap between  
**design-oriented modeling** and **engineering simulation**.

---

## CFD-Ready Geometry Preparation

Before simulation, the geometry was simplified and prepared specifically for CFD use.

Key decisions included:

- Closing and simplifying wheel arches  
- Cleaning and flattening underbody geometry  
- Removing fine decorative details that do not influence flow behavior  
- Including a ground plane for external aerodynamics studies  

The final geometry was exported as a **watertight STL**, suitable for unstructured meshing using **cfMesh**.

---

## CFD Pipeline Overview

The project uses a fully open-source CFD workflow:

← [Back to Projects](/projects/)
