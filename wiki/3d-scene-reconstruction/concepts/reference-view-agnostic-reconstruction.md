---
topic: 3d-scene-reconstruction
tags: [concept, principle]
---

## Definition

Reference-view-agnostic reconstruction is the principle of predicting 3D geometry from image collections without designating a fixed reference frame. Classically, Structure-from-Motion (SfM) and Multi-view Stereo (MVS) methods choose one image as the reference, establish a coordinate system anchored to that view's camera frame, and compute all other cameras' extrinsics and points relative to it. Reference-agnostic approaches instead predict geometry in a way that is symmetric across all images—no single view is privileged. In practice, this often means predicting quantities in each frame's own coordinate system or using representations that are invariant to the choice of reference frame (e.g., affine-invariant camera poses).

## Origins

The practice of choosing a reference view comes from classical SfM pipelines (Hartley & Zisserman, Frahm et al.) where it was natural: compute relative poses between image pairs, then chain them into a single global coordinate system. Modern deep learning methods (DUSt3R, VGGT, Fast3R) inherited this design choice despite having no fundamental reason for it—neural networks can predict geometry in arbitrary coordinate systems. π³ demonstrates that reference-view selection actually degrades performance and robustness, motivating a shift toward symmetric prediction.

## Key variants / extensions

- **Relative pose representation**: Predict pairwise pose differences without anchoring to a global frame; still requires reference-agnostic post-processing to convert to a global system if needed
- **Canonical coordinate system**: Predict geometry in a learned, data-dependent canonical frame (e.g., the "average" or "principal" view) rather than an arbitrary fixed reference
- **Multi-reference reasoning**: Predict geometry under multiple hypothetical reference frames and aggregate for robustness (computationally expensive)
- **Absolute pose with scale recovery**: π³'s approach; predict affine-invariant (reference-agnostic) poses and scale-invariant depths, then optionally recover metric scale from additional signals

## Papers using this concept

- [[../papers/2026-pi3-permutation-equivariant-visual-geometry-learning|π³: Permutation-Equivariant Visual Geometry Learning]] — core contribution; eliminates reference-view bias by predicting camera poses in a frame-independent manner; demonstrates 8× robustness improvement over reference-dependent methods and consistent SOTA performance across benchmarks
