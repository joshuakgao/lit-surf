# Depth Estimation — Index

Monocular depth estimation is the task of predicting dense 3D geometry from a single image. This wiki tracks literature on depth and surface normal estimation, with emphasis on foundation models, zero-shot generalization, and leveraging pre-trained generative priors (diffusion models, image editors) for robust geometric prediction with minimal task-specific supervision.

## Papers by year

### 2026
- [[papers/2026-fe2e-from-editor-to-dense-geometry-estimator|FE2E: From Editor to Dense Geometry Estimator]] — DiT-based editing model adapted for zero-shot depth/normal estimation, achieving 35% improvements on ETH3D with 100× less training data than DepthAnything
<img src="/wiki/depth-estimation/papers/2026-fe2e-from-editor-to-dense-geometry-estimator.png" height="300"/>

## Concepts
- [[concepts/monocular-depth-estimation|Monocular Depth Estimation]] — Predicting dense depth from a single RGB image
- [[concepts/dense-prediction|Dense Prediction]] — Per-pixel or per-voxel prediction tasks (depth, segmentation, normals, optical flow)
- [[concepts/zero-shot-learning|Zero-Shot Learning]] — Performing tasks without task-specific training examples

## See also
- [[../3d-scene-understanding/index|3D Scene Understanding]] — Depth is foundational for 3D reconstruction and scene understanding
- [[../denoising-segmentations/index|Denoising Segmentations]] — Related dense prediction task with complementary challenges
