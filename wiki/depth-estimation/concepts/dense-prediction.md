---
topic: depth-estimation
tags: [concept, task]
---

## Definition

Dense prediction refers to per-pixel or per-voxel prediction tasks where every spatial location in the input receives an output prediction. Common examples include semantic segmentation (class per pixel), depth estimation (depth value per pixel), surface normal estimation (normal vector per pixel), and optical flow (motion vector per pixel). Dense prediction tasks contrast with sparse tasks like object detection (bounding boxes) or classification (single output per image).

## Origins

Dense prediction became a central computer vision task after fully convolutional networks (FCN, 2015) showed that convolutional architectures could be adapted for pixel-level outputs. Modern approaches leverage multi-scale feature hierarchies, skip connections, and learned priors.

## Key variants / extensions

- **Geometric dense prediction**: Depth, normals, optical flow (geometry-specific tasks)
- **Semantic dense prediction**: Segmentation, scene parsing (category labels per pixel)
- **Hybrid**: Panoptic segmentation (combining instance + semantic dense prediction)
- **Using generative priors**: Leveraging diffusion models or editing models to learn output space priors

## Papers using this concept

- [[2026-fe2e-from-editor-to-dense-geometry-estimator]] — Shows image editing models are better-suited foundations for dense geometric prediction than T2I generators
