---
topic: point-cloud-registration
tags: [concept, method]
---

## Definition

Superpoint matching is a coarse-to-fine strategy for point cloud registration that first establishes correspondences between downsampled geometric patches (superpoints) in two point clouds, then propagates these matches to individual dense points. Rather than matching individual points or detecting repeatable keypoints, superpoints are matched based on whether their local neighborhoods (patches) overlap spatially.

## Origins

Emerged from image matching literature and adapted to 3D point clouds by methods seeking to avoid the repeatability requirement of keypoint detection—a major challenge in low-overlap scenarios. [[papers/2023-geotransformer|GeoTransformer]] demonstrates effective superpoint matching using geometric transformers.

## Key variants / extensions

- **Patch-level matching**: Matching based on overlapping local neighborhoods rather than individual point correspondences
- **Propagation strategies**: Dense point correspondences derived from superpoint matches; quality depends on superpoint matching accuracy
- **Learned superpoint selection**: Data-driven methods for determining which points to use as superpoints vs. traditional downsampling

## Papers using this concept

- [[papers/2023-geotransformer|GeoTransformer (2023)]] — Uses superpoint (patch) matching as first stage; propagates to dense 500-point correspondences
