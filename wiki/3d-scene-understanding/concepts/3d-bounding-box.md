---
topic: 3d-scene-understanding
tags: [concept, method]
---

## Definition

A 3D bounding box (3DBB) is an axis-aligned or oriented rectangular box in 3D space that tightly encloses an object. An **oriented bounding box (OBB)** additionally encodes the object's rotation, represented as a quaternion or rotation matrix. Full parameterization includes center (x, y, z), dimensions (width, height, depth), and orientation.

## Origins

Classical concept in 3D computer vision and robotics, dating back to CAD-based object recognition. Modern instantiation in deep learning-based 3D object detection (FRUSTUM PointNets, 3D R-CNN, etc.) and autonomous driving (YOLO 3D, Waymo's 3D detectors).

## Key variants / extensions

- **Axis-aligned bounding boxes (AABB)**: Simplified variant; orientation fixed to world frame axes. Easier to compute but less tight fit for rotated objects
- **Oriented bounding boxes (OBB)**: Rotation-aware; better fit and representation of object geometry
- **Instance segmentation + 3D shape prior**: Rather than a single box, some methods predict per-object 3D shapes or meshes (e.g., from CAD models)
- **Camera-aware lifting**: Recent trend (Boxer, 2026) to infer 3D OBBs from 2D detections using camera intrinsics and geometric constraints

## Papers using this concept

- [[2026-boxer-lifting-2d-to-3d|Boxer]] — predicts full 3D OBBs (center, dimensions, quaternion) per 2D detection via cross-attention over camera and depth
- [[2025-spatiallm-structured-indoor-modeling|SpatialLM]] — encodes detected 3D objects as text parameters (3D bounding boxes + semantic labels)
