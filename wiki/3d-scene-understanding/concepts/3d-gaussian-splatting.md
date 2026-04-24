---
topic: 3d-scene-understanding
tags: [concept, architecture]
---

## Definition

3D Gaussian Splatting (3DGS) is a neural rendering technique that represents 3D scenes as a set of learnable 3D Gaussian primitives. Each Gaussian is parameterized by position, covariance (controlling size and orientation), color (SH coefficients), and opacity. During rendering, Gaussians are projected to 2D, rasterized, and composited via alpha blending. This approach achieves real-time rendering speeds (30+ fps) while maintaining photorealistic visual quality comparable to or exceeding NeRF-based methods. 3DGS is widely adopted in visual effects, gaming, and interactive 3D applications because it avoids the computational overhead of volumetric ray marching.

## Origins

Introduced in "3D Gaussian Splatting for Real-Time Radiance Field Rendering" by Kerbl et al. (2023). The paper demonstrated that 3DGS achieves state-of-the-art novel-view synthesis quality with training times under an hour and real-time rendering, making it a paradigm shift for neural 3D representations.

## Key variants / extensions

- **Dynamic 3DGS**: Extend static Gaussians to model temporal motion; support deformation over time or dynamic scene capture.
- **Interactive editing**: Methods for segmenting and manipulating individual objects within a 3DGS representation (e.g., B³-Seg for semantic labels; interactive deletion/relocation of Gaussians).
- **Open-vocabulary labeling**: Assigning semantic labels to Gaussians via 2D foundation models (e.g., CLIP, Grounding DINO); enables zero-shot scene understanding.
- **3DGS reconstruction**: End-to-end methods that optimize Gaussians directly from multi-view images, replacing traditional MVS + NeuS pipelines.
- **Hybrid representations**: Combining 3DGS with explicit geometry (mesh, octree) or other neural fields for specific properties.

## Papers using this concept

- [[2026-b3seg-camera-free-3dgs-segmentation]] — applies Beta–Bernoulli Bayesian updates to assign object labels to 3DGS Gaussians via active view selection
