# Depth Estimation — Index

Monocular depth estimation is the task of predicting dense 3D geometry from a single image. This wiki tracks literature on depth and surface normal estimation, with emphasis on foundation models, zero-shot generalization, and leveraging pre-trained generative priors (diffusion models, image editors) for robust geometric prediction with minimal task-specific supervision.

## Papers by year

### 2026
- [[papers/2026-fe2e-from-editor-to-dense-geometry-estimator|FE2E: From Editor to Dense Geometry Estimator]] — DiT-based editing model adapted for zero-shot depth/normal estimation, achieving 35% improvements on ETH3D with 100× less training data than DepthAnything
<img src="/raw/depth-estimation/2026/thumbnails/2026-fe2e-from-editor-to-dense-geometry-estimator.png" height="300"/>

### 2024
- [[papers/2024-depth-anything-v2|Depth Anything V2]] — Replaces real labeled images with synthetic for precision, scales teacher model, bridges synthetic-to-real via pseudo-labeled images; achieves fine-grained details comparable to diffusion models with 10× faster inference
<img src="/raw/depth-estimation/2024/thumbnails/2024-depth-anything-v2.png" height="300"/>
- [[papers/2024-depth-anything|Depth Anything: Unleashing the Power of Large-Scale Unlabeled Data]] — Foundation model via self-training on 62M unlabeled images with strong perturbations; outperforms MiDaS zero-shot across six benchmarks
<img src="/raw/depth-estimation/2024/thumbnails/2024-depth-anything.png" height="300"/>

## Concepts
- [[concepts/monocular-depth-estimation|Monocular Depth Estimation]] — Predicting dense depth from a single RGB image
- [[concepts/dense-prediction|Dense Prediction]] — Per-pixel or per-voxel prediction tasks (depth, segmentation, normals, optical flow)
- [[concepts/zero-shot-learning|Zero-Shot Learning]] — Performing tasks without task-specific training examples
- [[concepts/self-training|Self-Training]] — Using model predictions as pseudo-labels for unlabeled data; requires strong perturbations to unlock benefits
- [[concepts/pseudo-labeling|Pseudo-Labeling]] — Automatic label generation for unlabeled data using pre-trained models

## See also
- [[../3d-scene-understanding/index|3D Scene Understanding]] — Depth is foundational for 3D reconstruction and scene understanding
- [[../denoising-segmentations/index|Denoising Segmentations]] — Related dense prediction task with complementary challenges
