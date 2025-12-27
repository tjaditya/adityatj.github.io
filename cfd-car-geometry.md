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

**GitHub Repository:**  
👉 https://github.com/tjaditya/cfd-car-geometry
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

## CFD Meshing Strategy (snappyHexMesh)

Surface and volume meshes were generated using **snappyHexMesh**, selected for its ability to produce hex-dominant unstructured meshes around complex external geometries within an open-source CFD workflow.

The meshing strategy focused on:
- capturing global body curvature without excessive cell counts
- applying local refinement in aerodynamically sensitive regions (front fascia, roof, rear wake)
- maintaining mesh quality suitable for steady-state solvers

Rather than uniformly refining the entire domain, refinement regions were applied selectively. This reflects how CFD is used in early-stage aerodynamic exploration—balancing physical resolution, numerical stability, and computational efficiency.

At this stage, the objective was not high-fidelity force prediction, but the generation of a stable mesh capable of resolving major flow features and wake behavior.

---

## Mesh Quality Verification

Mesh quality was evaluated prior to simulation to ensure numerical robustness and solver stability.

Quality checks included:
- non-orthogonality
- skewness
- cell aspect ratios

The final mesh satisfied recommended quality thresholds for steady-state external aerodynamics using **simpleFoam**. While not optimized for precise aerodynamic coefficient prediction, the mesh was verified to be suitable for studying flow patterns, separation behavior, and wake structure.


![CFD mesh visualization](/assets/projects/cfd/results/mesh-1.png)

Surface and volume mesh visualization highlighting local refinement near the front fascia, roof, and rear wake region.

---

## Steady-State Flow Simulation Setup (OpenFOAM)

Flow simulations were performed using **OpenFOAM** with the **simpleFoam** solver, appropriate for steady-state, incompressible external aerodynamics.

Key setup elements included:
- uniform inlet velocity representing freestream conditions
- no-slip boundary condition on the vehicle surface
- fixed pressure outlet boundary condition
- turbulence modeling suitable for steady external flow studies

The objective of this phase was to establish a stable and converged solver configuration capable of producing physically interpretable flow fields, rather than absolute aerodynamic performance metrics.

---

## CFD Results and Convergence Validation

The steady-state solution converged after approximately 2000 SIMPLE iterations.

Convergence was assessed using:
- residual reduction for governing equations
- stabilization of integrated force coefficients over successive iterations

Both criteria were used together to distinguish numerical convergence from physically meaningful stabilization. This reinforced the understanding that residual decay alone is not sufficient to assess solution reliability.

![CFD convergence history](/assets/projects/cfd/results/convergence-combined.png)

Convergence history showing residual decay and force coefficient stabilization, confirming numerical and practical convergence of the steady-state solution.

---

## Flow Visualization and Qualitative Analysis (ParaView)

With a converged steady-state solution obtained, **ParaView** was used to perform qualitative flow analysis aimed at understanding three-dimensional flow behavior around the body.

Post-processing focused on:
- velocity magnitude contours to examine flow acceleration and deceleration over key surfaces  
- sectional velocity slices at multiple heights to study vertical variation in the flow field  
- streamline and streamtracer visualization to examine wake formation and recirculation behavior  

Rather than relying on a single visualization, multiple complementary views were used to build a physically consistent picture of the external flow.

### Velocity Distribution Across Vertical Sections

Horizontal velocity slices taken near the ground, at mid-height, and near the roof reveal how flow behavior evolves across the height of the body. Near-ground regions show reduced velocities influenced by boundary-layer effects and simplified underbody geometry. Mid-height slices capture smoother acceleration along the side surfaces, while roof-level slices exhibit the highest velocities, consistent with acceleration over curved upper surfaces.

Together, these comparisons highlight the dominant role of overall body curvature in governing flow attachment and wake development.

![Velocity magnitude – Roof section](/assets/projects/cfd/results/velocity-roof.png)
Velocity profile - Roof section
![Velocity magnitude – Mid section](/assets/projects/cfd/results/velocity-mid.png)
Velocity profile - Mid section
![Velocity magnitude – Ground section](/assets/projects/cfd/results/velocity-underbody.png)
Velocity profile - Underbody section

Velocity magnitude contours at multiple vertical sections, illustrating the evolution of flow acceleration from the ground plane to the roof.

### Mid-Plane and Side Periphery Flow Behavior

Additional velocity slices were extracted along the vehicle centerline and through the side periphery, intersecting the wing-like structural elements that emerge from the body, curve outward, and rejoin downstream as a continuous hoop-like form.

These sections were chosen to examine how localized three-dimensional geometry influences flow acceleration, deviation, and interaction with the surrounding flow field. The mid-plane slice provides a reference view of overall flow attachment and separation along the primary flow direction, while the periphery slice captures the effect of the wing–hoop structure on local velocity distribution and flow redirection.

The periphery slice highlights regions of localized acceleration and flow curvature induced by the side-mounted feature, illustrating how such geometry introduces three-dimensional effects even in an otherwise symmetric external flow. Together, these views emphasize how secondary design elements can influence local flow behavior without dominating overall wake structure.

![Velocity magnitude – vertical mid-plane slice](/assets/projects/cfd/results/velocity-vertical-slice-mid.png)
![Velocity magnitude – vertical periphery slice](/assets/projects/cfd/results/velocity-vertical-slice-periphery.png)

Velocity magnitude slices through the vehicle mid-plane and side periphery, illustrating localized flow behavior influenced by the wing–hoop structural geometry.


### Wake Structure and Streamtracer Visualization

To further examine wake behavior, streamtracer visualization was used to track flow paths downstream of the vehicle. Seed points placed upstream of the body reveal how flow separates at the rear surfaces and forms recirculation regions in the wake.

The streamtracers make the three-dimensional nature of the wake more apparent than scalar contours alone, highlighting regions of flow reversal, mixing, and gradual recovery toward freestream conditions. This view complements the velocity slice analysis by providing an intuitive visualization of wake size, structure, and coherence.

![Wake streamtracer visualization](/assets/projects/cfd/results/wake-streamtracers.png)

Streamtracer visualization showing flow separation and recirculation in the vehicle wake, illustrating wake structure and downstream recovery.

Overall, these visualizations were used to connect geometric design decisions to observed flow behavior, reinforcing CFD’s role as an exploratory and interpretive tool during early-stage aerodynamic development.

### Pressure Field Visualization and Wake Correlation

To complement the velocity-based analysis, a three-dimensional pressure field visualization was examined to better understand the relationship between surface geometry and wake formation.

The pressure distribution highlights higher-pressure regions near the frontal surfaces and a pronounced low-pressure zone in the rear wake. This pressure deficit downstream of the body is consistent with the observed flow separation and recirculation patterns identified in the velocity slices and streamtracer visualizations.

Rather than serving as a basis for quantitative force estimation, the pressure field is used here to reinforce physical intuition—illustrating how pressure gradients drive flow separation and influence wake structure in external aerodynamics.

![3D pressure field visualization](/assets/projects/cfd/results/pressure-field-3d.png)

Three-dimensional pressure field visualization showing frontal pressure buildup and low-pressure regions in the vehicle wake, correlated with observed flow separation and recirculation.

---

## Interpretation and Engineering Insights

This project demonstrated how design intent, geometric discipline, and simulation are tightly coupled in early-stage engineering workflows.

The CFD results show smooth acceleration of flow over the hood and roof, indicating that the refined surface continuity achieved during Blender-based modeling supports largely attached flow across the upper body. In contrast, flow separation and a low-velocity wake form near the rear of the vehicle, highlighting the dominant influence of rear geometry on wake structure and pressure recovery.

Importantly, these flow features were consistent with both physical intuition and observations made during the 3D-printed prototype review. Surface transitions that appeared abrupt or visually ambiguous in early physical prints correspond to regions of increased flow disturbance in the simulation, reinforcing the value of combining physical prototyping with computational analysis.

From an engineering perspective, this phase reinforced several key lessons:
- clean, watertight geometry is essential for stable meshing and solver convergence  
- mesh resolution and refinement choices directly influence which flow features can be meaningfully interpreted  
- numerical convergence is a prerequisite for analysis, but does not guarantee physical accuracy  
- CFD is most effective as a comparative and exploratory tool rather than an absolute predictor in early design stages  

Overall, the project established a repeatable, open-source pipeline that links concept design, physical feedback, and computational analysis. This foundation enables systematic geometry iteration and provides a framework for deeper aerodynamic studies in future phases.

---

## Next Technical Focus

With the CFD pipeline successfully established and validated, active development on this project is now paused. The primary focus has shifted toward a Raspberry Pi–based autonomous rover project, where attention is directed to real-time sensing, control, and embedded systems.

The CFD pipeline developed here remains available as a reusable framework for future design studies or comparative analysis, should the need arise.

---

## Potential Extensions
- Comparitive study with the modified model
- Extraction of basic aerodynamic coefficients for relative comparison
- Controlled geometry variations to study qualitative aerodynamic trends


[Back to Projects](/projects/)
