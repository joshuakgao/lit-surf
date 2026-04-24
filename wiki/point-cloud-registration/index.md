# Point Cloud Registration — Index

Point cloud registration is the problem of estimating a rigid (or non-rigid) transformation that aligns two or more partially overlapping 3D point clouds. This is fundamental to 3D reconstruction, mapping, localization, and robotics. Recent advances focus on learning-based correspondence methods that bypass the difficulties of keypoint detection, especially in challenging low-overlap and symmetric scenarios.

## Papers by year

### 2023
- [[papers/2023-geotransformer|GeoTransformer: Fast and Robust Point Cloud Registration with Geometric Transformer]] — Geometric transformer for robust superpoint matching in low-overlap cases; achieves RANSAC-free registration with 100× speedup
<img src="/raw/point-cloud-registration/2023/thumbnails/2023-geotransformer.png" height="300"/>

### 2019
- [[papers/2019-deep-closest-point|Deep Closest Point: Learning Representations for Point Cloud Registration]] — End-to-end learnable reimagining of ICP using attention-based soft matching and differentiable SVD; succeeds on large transformations and sharp features
<img src="/raw/point-cloud-registration/2019/thumbnails/2019-deep-closest-point.png" height="300"/>

## Concepts
- [[concepts/superpoint-matching|Superpoint Matching]] — Coarse-to-fine matching of downsampled point patches
- [[concepts/geometric-consistency|Geometric Consistency]] — Spatial constraints for robust correspondence

## See also
- [[../3d-scene-understanding/index|3D Scene Understanding]] — Related applications of 3D geometry
- [[../visual-localization/index|Visual Localization]] — Uses point cloud registration for place recognition
