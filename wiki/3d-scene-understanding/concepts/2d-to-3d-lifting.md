---
topic: 3d-scene-understanding
tags: [concept, method]
---

## Definition

2D-to-3D lifting is the problem of predicting metric 3D geometry (position, size, orientation) from 2D image observations and optional depth cues. Rather than detecting objects directly in 3D space, lifting decouples the problem: use a 2D detector to localize objects in the image plane, then predict their full 3D parameters conditioned on image features, camera intrinsics, and depth. This approach allows models to leverage the scale and diversity of open-vocabulary 2D detectors while specializing in geometric prediction.

## Origins

The 2D-to-3D lifting formulation is formalized in CuTR (2024), which uses a DETR-style transformer to lift 2D boxes from egocentric video into 3D. Boxer (2026) generalizes and scales this approach, showing that lifting works across camera types, depth modalities, and open-world object categories at scale.

## Key variants / extensions

- **Monocular lifting**: Predict 3D from 2D alone without depth; inherently ambiguous and relies on dataset priors
- **Depth-conditioned lifting**: Use optional sparse point clouds or dense depth maps to reduce geometric ambiguity; enables metric scale prediction
- **Multi-view fusion**: Merge per-frame 3D predictions across video or multi-camera sequences using geometric consistency and Hungarian matching
- **Open-vocabulary lifting**: Apply lifting to arbitrary object categories via text-prompted 2D detectors (OWLv2, DETIC); enables zero-shot 3D detection

## Papers using this concept

- [[2026-boxer-lifting-2d-to-3d]] — generalizes lifting to open-world objects with flexible depth modalities and multi-view fusion
