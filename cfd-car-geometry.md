---
layout: page
title: Concept Car Geometry Development and CFD Pipeline Implementation
permalink: /projects/cfd-car-geometry/
---
<script type="module" src="https://unpkg.com/@google/model-viewer/dist/model-viewer.min.js"></script>

[Back to Projects](/projects/)

Tools: Blender, snappyHexMesh, OpenFOAM, ParaView, 3D Printing  
Domain: Automotive Design and Aerodynamics  
Type: Self-driven follow-up project  
Status: Phase 1 complete (digital-to-physical workflow established; CFD pipeline converged)

---

## Project Context

This project is a follow-up to a 3-week onsite summer course in "Introduction to Car Design" at Istituto Europeo di Design (IED), Turin.

The objective was to take an early-stage concept design and develop it into:
- a CFD-ready 3D geometry suitable for airflow analysis, and
- a complete open-source CFD workflow that can be repeated and improved through iteration.

In addition to the digital pipeline, I 3D printed the geometry, incorporated faculty feedback, and produced a modified second iteration.

---

## Concept and Early Form Exploration

The initial phase focused on exploring overall proportions, stance, and surface flow in Blender.

Key areas of attention:
- wheel arch placement
- frontal intake shaping
- roof curvature and rear taper

At this stage, the emphasis was on form exploration without constraining the design too early based on simulation limitations.

![Concept form exploration in Blender](/assets/projects/cfd/screenshots/01-concept-form.png)

Early concept-stage form exploration in Blender, focusing on proportions, stance, and overall surface flow before applying simulation constraints.

---

## Full Body Surface Development

The concept was progressively refined into a continuous full-body shell.

Key refinements included:
- smoothing abrupt curvature transitions
- improving surface continuity across major panels
- eliminating visually appealing but non-physical sharp edges

These changes were made with the understanding that surface quality directly impacts CFD mesh stability and solver robustness.

![Refined surface development](/assets/projects/cfd/screenshots/02-surface-refinement.png)

Progressive refinement into a continuous body shell, improving curvature continuity and eliminating sharp, non-physical transitions.

---

## Topology and Mesh-Aware Modeling

Once the overall form was established, the model was reworked with mesh awareness in mind.

Steps taken:
- clean and consistent topology aligned with surface curvature
- removal of non-manifold edges
- reduction of unnecessary geometric complexity
- preparation for watertight surface export

This phase was critical in bridging the gap between design-oriented modeling and engineering simulation.

![Mesh-aware topology cleanup](/assets/projects/cfd/screenshots/03-topology-cleanup.png)

Topology cleanup and edge-flow alignment performed with mesh stability and CFD suitability in mind.

<section style="margin: 1.5rem 0;">
  <h2>Interactive Geometry</h2>
  <p>
    The interactive model below shows the external body geometry used for CFD analysis and physical prototyping.
    It is intended to highlight surface continuity and curvature transitions before meshing and simulation.
  </p>

  <model-viewer
    src="/assets/projects/cfd/models/car-body.glb"
    alt="Concept car external body geometry (CFD-ready)"
    camera-controls
    interaction-prompt="auto"
    shadow-intensity="0"
    exposure="1"
    ar
    ar-modes="webxr scene-viewer quick-look"
    style="
      width: 100%;
      max-width: 960px;
      height: 520px;
      background: #f6f6f6;
      border: 1px solid #e5e5e5;
      border-radius: 12px;
      display: block;
      margin: 1rem 0;
    ">
  </model-viewer>

  <p style="font-size: 0.95rem; opacity: 0.85; margin-top: 0.25rem;">
    Tip: drag to rotate, scroll to zoom, right-drag to pan.
  </p>

  <noscript>
    <p>
      Interactive 3D preview requires JavaScript. You can download the model here:
      <a href="/assets/projects/cfd/models/car-body.glb">car-body.glb</a>
    </p>
  </noscript>
</section>
---

## Physical Prototyping and Feedback-Driven Iteration (3D Printing)

To complement the digital workflow, I 3D printed the car model through an external vendor to validate proportions, surface continuity, and manufacturability.

After reviewing the first print, I received feedback from an IED faculty mentor related to surface coherence and overall form.

Based on that feedback, I modified the 3D geometry and produced a second iteration, which was also 3D printed. This reinforced an iterative engineering mindset where critique and physical validation inform the next design version.

Optional images to add in this section:
- first print photo: /assets/projects/cfd/prints/print-v1.jpg
- second print photo: /assets/projects/cfd/prints/print-v2.jpg
- side-by-side comparison: /assets/projects/cfd/prints/print-compare.jpg

---

## CFD Pipeline Overview

This project extends beyond geometry preparation into a complete open-source CFD workflow for external aerodynamics.

Pipeline:

    Blender (.blend)
      -> STL export
      -> snappyHexMesh (surface and volume meshing)
      -> OpenFOAM (steady-state solver: simpleFoam)
      -> ParaView (flow visualization and analysis)

---

## Geometry Export and Technical Pre-processing

The finalized external body shell was prepared in Blender and exported as a watertight STL for external aerodynamics analysis.

At this stage, the focus was on producing a clean, simulation-ready geometry rather than a visually complete vehicle model. The geometry represents an abstracted aerodynamic body suitable for stable meshing and solver convergence.

Key pre-processing decisions:
- ensuring a fully closed, watertight external surface suitable for volume meshing
- verification and correction of surface normal orientation across the entire body
- removal of fine decorative features that do not meaningfully influence external flow
- removal of wheels and ground plane to simplify the problem and isolate body-driven flow effects
- simplification of underbody geometry to avoid unnecessary meshing complexity
- alignment of the geometry with the global coordinate system for consistent CFD domain setup

By excluding wheels and ground interaction at this phase, the simulation remains computationally tractable and well-suited for studying baseline flow behavior, separation, and wake structure around the body.

---

### Final External Body Shell (CFD-ready)

![Final CFD-ready external body shell](/assets/projects/cfd/screenshots/06-final-cfd-body-shell.png)

Final external body geometry after cleanup and simplification. Wheels and ground plane have been removed to isolate the aerodynamic influence of the body shape.

---

### Surface Closure and Normal Orientation Verification

![Watertight surface and normal direction verification](/assets/projects/cfd/screenshots/05-geometry-watertight-check.png)

Inspection of the closed external body shell in Blender with face normal visualization enabled. Surface normals were checked and corrected to ensure consistent outward orientation, preventing meshing and solver instability.

---

## Meshing with snappyHexMesh

Unstructured surface and volume meshes are generated using snappyHexMesh, with focus on:
- adequate surface resolution to capture curvature
- local refinement near critical regions (front fascia, roof, rear wake region)
- maintaining reasonable cell counts for computational efficiency
- ensuring mesh quality suitable for steady-state solvers

Mesh quality is evaluated using standard metrics (for example, skewness and non-orthogonality) before proceeding to simulation.

---

## Mesh Quality Summary

Mesh quality was evaluated prior to simulation to ensure numerical stability.

Key mesh characteristics:
- unstructured hex-dominant mesh generated using snappyHexMesh
- local refinement near the front fascia, roof, and rear wake region
- quality checks performed for skewness and non-orthogonality

The mesh quality was verified to be numerically suitable for steady-state solver convergence using simpleFoam.

![CFD mesh visualization](/assets/projects/cfd/results/mesh.png)

Surface and volume mesh visualization highlighting refinement regions.

---

## Flow Simulation with OpenFOAM

Simulations are performed using OpenFOAM, currently focusing on steady-state external flow using the simpleFoam solver.

Key aspects include:
- inlet velocity boundary conditions representing uniform freestream flow
- no-slip conditions on the vehicle surface
- outlet pressure boundary conditions
- turbulence modeling appropriate for steady-state external automotive flow studies

The emphasis at this stage is on solver setup, stability, and convergence behavior rather than absolute aerodynamic coefficients.

---

## CFD Results and Convergence Validation

The steady-state simulation reached numerical convergence after approximately 2000 SIMPLE iterations.

Convergence was assessed using:
- residual reduction for governing equations, and
- stabilization of integrated force coefficients over successive iterations

![CFD convergence summary showing residual and force coefficient histories](/assets/projects/cfd/results/convergence-combined.png)

Convergence history showing residual decay and force coefficient stabilization, confirming numerical and practical convergence of the steady-state solution.

---

## Post-processing and Flow Interpretation (ParaView)

With a converged steady-state solution obtained, ParaView is used primarily for qualitative flow interpretation.

Post-processing focuses on:
- velocity magnitude contours to identify acceleration and deceleration regions
- streamline analysis to examine flow attachment and separation behavior
- visualization of wake structure and recirculation zones behind the vehicle
- qualitative comparison of flow features between geometry iterations

Key qualitative observations include:
- flow acceleration over the hood and roof
- separation and wake formation behind the vehicle
- regions of reduced velocity and recirculation in the rear wake

The emphasis at this stage is on developing physical intuition and understanding how design features influence external aerodynamics.

---

## Engineering Takeaways

This phase of the project reinforced several key engineering lessons:
- clean surface geometry is critical for stable meshing and solver convergence
- physical prototypes can reveal design issues not obvious in purely digital workflows
- feedback-driven iteration improves both form quality and simulation readiness
- numerical convergence does not guarantee physical accuracy, but it is a necessary first step
- CFD is most effective when used comparatively, not as an absolute predictor

---

## Next Technical Focus

With the CFD pipeline successfully established and converged, current efforts are focused on:
- interpreting flow features and wake behavior
- studying sensitivity to meshing and boundary conditions
- planning controlled geometry modifications for comparative analysis
- building confidence in linking design changes to aerodynamic trends

---

## Planned Extensions

Future extensions of this work include:
- mesh refinement and grid sensitivity studies
- extraction of pressure coefficients and aerodynamic forces
- comparative analysis between multiple design iterations
- exploration of data-driven or AI-assisted surrogate models for rapid evaluation

[Back to Projects](/projects/)
