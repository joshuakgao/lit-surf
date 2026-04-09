---
topic: 3d-scene-understanding
tags: [concept, method]
---

## Definition

Multi-view fusion combines detections or reconstructions from multiple camera viewpoints to produce a globally consistent, unified representation. For 3D object detection, this typically means merging per-frame detections across a video sequence or multi-camera rig to reduce duplicate detections, resolve ambiguities, and improve localization accuracy.

## Origins

Classical in multi-view geometry and structure-from-motion (Hartley & Zisserman, 2003). Modern application to 3D object detection in autonomous driving and robotics (e.g., NMS across LiDAR + camera detections, temporal tracking).

## Key variants / extensions

- **Offline fusion**: Batch processing all frames to find optimal assignments (e.g., Hungarian matching). Higher latency but globally optimal
- **Online tracking**: Frame-by-frame assignment using Kalman filtering or attention-based correspondence. Lower latency, suitable for real-time systems
- **Geometry-aware fusion**: Accounts for camera poses and 3D geometry when merging detections (e.g., reprojection error); more principled than appearance-only matching
- **Temporal tracking**: Extends fusion to encode object trajectories and motion priors (e.g., constant velocity assumption in Kalman filters)

## Papers using this concept

- [[2026-boxer-lifting-2d-to-3d|Boxer]] — uses Hungarian-algorithm-based offline fusion and online tracking to merge per-frame 3D detections into scene-level consistent boxes
- [[2025-spatiallm-structured-indoor-modeling|SpatialLM]] — fuses point cloud frames via voxelization and spatial pooling, implicitly merging multi-view observations
