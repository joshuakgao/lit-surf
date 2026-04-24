---
topic: depth-estimation
tags: [concept, task]
---

## Definition

Monocular depth estimation is the task of predicting a dense depth map from a single RGB image. Unlike stereo or multi-view depth estimation, monocular methods must infer 3D geometry from 2D image cues (shading, perspective, occlusion patterns, learned priors). This is an ill-posed problem requiring strong prior knowledge about scenes, objects, and physics.

## Origins

Early approaches relied on supervised learning on specific datasets (NYU Depth, KITTI). MiDaS (2019) pioneered zero-shot generalization across datasets through a multi-task framework. Recent advances use pre-trained generative models (Stable Diffusion, diffusion transformers) as geometry priors.

## Key variants / extensions

- **Supervised monocular depth**: Trained on labeled depth datasets with known ground truth
- **Zero-shot depth estimation**: Using pre-trained generative models without task-specific training
- **Self-supervised depth**: Learning from video sequences without explicit depth labels
- **Metric vs. relative depth**: Recovering absolute depth scale vs. relative scene geometry

## Papers using this concept

- [[2024-depth-anything]] — Foundation model via self-training on 62M unlabeled images; strong zero-shot generalization
- [[2026-fe2e-from-editor-to-dense-geometry-estimator]] — Achieves exceptional zero-shot monocular depth via editing model foundation, outperforming 100× larger supervised baselines
