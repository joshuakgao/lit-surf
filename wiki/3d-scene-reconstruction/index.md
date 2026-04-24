---
topic: 3d-scene-reconstruction
---

# 3D Scene Reconstruction — Index

Feed-forward neural approaches to dense 3D reconstruction from images: camera pose estimation, depth estimation, and 3D point prediction. Encompasses single-image, multi-view, and video reconstruction across diverse domains (indoor, outdoor, aerial, synthetic). Emphasis on eliminating inductive biases, achieving permutation invariance, and scaling to open-domain imagery without fine-tuning.

## Papers by year

### 2026
- [[papers/2026-dage-dual-stream-geometry-estimation|DAGE: Dual-Stream Architecture for Efficient and Fine-Grained Geometry Estimation]] — decouples global consistency (low-resolution stream) from fine detail (high-resolution stream) via lightweight cross-attention adapter; supports 2K resolution and 1000+ frames; 2-28x faster than prior SOTA with state-of-the-art depth sharpness
<img src="/raw/3d-scene-reconstruction/2026/thumbnails/2026-dage-dual-stream-geometry-estimation.png" height="300"/>

- [[papers/2026-pi3-permutation-equivariant-visual-geometry-learning|π³: Permutation-Equivariant Visual Geometry Learning]] — fully permutation-equivariant feed-forward reconstruction without reference-view bias; predicts affine-invariant camera poses and scale-invariant point maps; handles single images, videos, unordered sets; state-of-the-art on 10+ benchmarks
<img src="/raw/3d-scene-reconstruction/2026/thumbnails/2026-pi3-permutation-equivariant-visual-geometry-learning.png" height="300"/>

### 2025
- [[papers/2025-d4rt-efficiently-reconstructing-dynamic-scenes|D4RT: Efficiently Reconstructing Dynamic Scenes One Query at a Time]] — unified transformer for 4D reconstruction (depth + point tracks + camera) via efficient point-query interface; avoids dense per-frame decoding; SOTA on point clouds, tracking, camera estimation from single videos
<img src="/raw/3d-scene-reconstruction/2025/thumbnails/2025-d4rt-efficiently-reconstructing-dynamic-scenes.png" height="300"/>

## Concepts

- [[concepts/permutation-equivariance|Permutation Equivariance]] — model invariance to input ordering; enables order-independent geometry prediction
- [[concepts/reference-view-agnostic-reconstruction|Reference-View-Agnostic Reconstruction]] — predicting geometry without privileging a single reference frame; eliminates viewpoint selection bias

## See also

- [[../3d-scene-understanding/index|3D Scene Understanding]] — broader category encompassing scene graphs, semantic geometry, spatial reasoning
- [[../depth-estimation/index|Depth Estimation]] — specialized task; π³ unifies depth with camera pose and point reconstruction
