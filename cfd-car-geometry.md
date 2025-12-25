---
layout: page
title: Concept Car Geometry Development & CFD Pipeline Implementation
permalink: /projects/cfd-car-geometry/
---
← [Back to Projects](/projects/)

**Tools:** Blender · snappyHexMesh · OpenFOAM · ParaView
**Domain:** Automotive Design & Aerodynamics  
**Type:** Self-driven follow-up project  
**Status:** Phase 1 complete (CFD pipeline established and converged)

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

![Concept form exploration in Blender](/assets/projects/cfd/screenshots/01-concept-form.png)

*Early concept-stage form exploration in Blender, focusing on proportions, stance, and overall surface flow before applying simulation constraints.*

---

## Full Body Surface Development

The concept was progressively refined into a continuous full-body shell.

Key refinements included:

- Smoothing abrupt curvature transitions  
- Improving surface continuity across major panels  
- Eliminating visually appealing but non-physical sharp edges  

These changes were made with the understanding that  
**surface quality directly impacts CFD mesh stability and solution accuracy**.

![Refined surface development](/assets/projects/cfd/screenshots/02-surface-refinement.png)

*Progressive refinement into a continuous body shell, improving curvature continuity and eliminating sharp, non-physical transitions.*

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

![Mesh-aware topology cleanup](/assets/projects/cfd/screenshots/03-topology-cleanup.png)

*Topology cleanup and edge-flow alignment performed with mesh stability and CFD suitability in mind.*

---

## CFD-Ready Geometry Preparation

Before simulation, the geometry was simplified and prepared specifically for CFD use.

Key decisions included:

- Closing and simplifying wheel arches  
- Cleaning and flattening underbody geometry  
- Removing fine decorative details that do not influence flow behavior  
- Including a ground plane for external aerodynamics studies  

The final geometry was exported as a **watertight STL**, suitable for unstructured meshing using **snappyHexMesh**.

![Final CFD-ready geometry on ground plane](/assets/projects/cfd/screenshots/04-cfd-ready-geometry.png)

*Final watertight geometry placed on a ground plane, prepared for STL export and unstructured meshing using snappyHexMesh.*

---

## CFD Pipeline Overview

This project extends beyond geometry preparation into a complete **open-source CFD workflow**,
built to study external aerodynamics of the concept vehicle.

The pipeline integrates **geometry preparation, meshing, simulation, and post-processing** as a
single end-to-end process.

```text
Blender (.blend)
↓ STL export
snappyHexMesh (surface & volume meshing)
↓
OpenFOAM (steady-state solver – simpleFoam)
↓
ParaView (flow visualization & analysis)
```

---

### Geometry Export & Pre-processing

The finalized car body is exported from Blender as a **watertight STL** with simplified features
appropriate for external aerodynamics studies.

Pre-processing considerations include:

- Consistent surface normals
- Removal of small geometric details that do not influence flow
- Placement on a ground plane to simulate road interaction
- Alignment with the global coordinate system for CFD domain setup

---

### Meshing with snappyHexMesh

Unstructured surface and volume meshes are generated using **snappyHexMesh**, with focus on:

- Adequate surface resolution to capture curvature
- Local refinement near critical regions (front fascia, roof, rear)
- Maintaining reasonable cell counts for computational efficiency
- Ensuring mesh quality suitable for steady-state solvers

Mesh quality is evaluated using standard metrics such as skewness and non-orthogonality
before proceeding to simulation.

---

## Mesh Quality Summary

Mesh quality was evaluated prior to simulation to ensure numerical stability.

Key mesh characteristics:
- Unstructured hex-dominant mesh generated using **snappyHexMesh**
- Local refinement near the front fascia, roof, and rear wake region
- Quality checks performed for skewness and non-orthogonality

The mesh was found to be suitable for steady-state external aerodynamics studies using `simpleFoam`.

![CFD mesh visualization](/assets/projects/cfd/results/mesh.png)

*Surface and volume mesh visualization highlighting refinement regions.*

---

### Flow Simulation with OpenFOAM

Simulations are performed using **OpenFOAM**, currently focusing on **steady-state external flow**
using the `simpleFoam` solver.

Key aspects include:

- Inlet velocity boundary conditions representing uniform freestream flow
- No-slip conditions on the vehicle surface
- Appropriate outlet pressure conditions
- Turbulence modeling appropriate for steady-state external automotive flow studies

The emphasis at this stage is on **solver setup, stability, and convergence behavior**, rather than
absolute aerodynamic coefficients.

---

## CFD Results & Convergence Validation

The steady-state simulation reached **mathematical convergence after approximately 2000 iterations** for the chosen solver and mesh configuration.

Convergence assessment was based on:
- Reduction of solver residuals by multiple orders of magnitude
- Stabilization of force coefficients over successive iterations

This confirmed that the solver setup, mesh, and boundary conditions were internally consistent and numerically stable for steady-state external flow analysis.

![Residuals and force convergence](/assets/projects/cfd/results/convergence.png)

*Representative residual and force coefficient convergence history for the steady-state simulation.*

---

### Post-processing & Flow Interpretation (ParaView)

With a converged steady-state solution obtained, **ParaView** is used primarily for
**qualitative flow interpretation**, rather than exploratory visualization.

Post-processing focuses on:

- Velocity magnitude contours to identify acceleration and deceleration regions
- Streamline analysis to examine flow attachment and separation behavior
- Visualization of wake structure and recirculation zones behind the vehicle
- Qualitative comparison of flow features between geometry iterations

Key qualitative observations include:
- Flow acceleration over the hood and roof
- Separation and wake formation behind the vehicle
- Regions of reduced velocity and recirculation in the rear wake

The emphasis at this stage is on **developing physical intuition** and understanding how
design features influence external aerodynamics, rather than extracting precise
aerodynamic coefficients.

---

## Engineering Takeaways

This phase of the project reinforced several key engineering lessons:

- Clean surface geometry is critical for stable meshing and solver convergence  
- Small design features can significantly influence wake structure  
- Numerical convergence does not guarantee physical accuracy, but is a necessary first step  
- CFD is most effective when used comparatively, not as an absolute predictor  

These insights now guide how I approach further design iterations and analysis.

---

## Next Technical Focus

With the CFD pipeline successfully established and converged, current efforts are focused on:

- Interpreting flow features and wake behavior
- Studying sensitivity to meshing and boundary conditions
- Planning controlled geometry modifications for comparative analysis
- Building confidence in linking design changes to aerodynamic trends

---

## Planned Extensions

Future extensions of this work include:

- Mesh refinement and grid sensitivity studies
- Extraction of pressure coefficients and aerodynamic forces
- Comparative analysis between multiple design iterations
- Exploration of data-driven or AI-assisted surrogate models for rapid evaluation

← [Back to Projects](/projects/)
