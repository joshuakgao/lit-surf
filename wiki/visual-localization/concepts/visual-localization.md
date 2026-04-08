---
topic: visual-localization
tags: [concept, task]
---

## Definition

Visual localization is the task of determining the 6-Degree-of-Freedom (6-DoF) pose (position and orientation) of a camera within a scene, given an RGB image and a reference 3D model. The pose is typically represented as a 3x4 camera matrix or translation + rotation parameters. Visual localization is a fundamental capability for robotics, AR/VR, autonomous systems, and 3D reconstruction.

## Origins

Visual localization has been studied for decades in photogrammetry and computer vision. Classical approaches used hand-crafted features (SIFT, SURF) for matching. Recent advances leverage learned CNN features for improved robustness to appearance changes.

## Key variants / extensions

- **6-DoF localization**: Full pose estimation (3D position + rotation)
- **Structure-based localization**: Matching against a sparse 3D SfM model (direct matching approach)
- **Image-based localization**: Matching against database images (retrieval-based approach)
- **Hierarchical localization**: Two-stage process combining coarse global retrieval and fine local matching
- **Pose regression**: Direct CNN regression of pose from image (less accurate but computationally efficient)

## Papers using this concept

- [[2019-hierarchical-localization-at-large-scale]] — Proposes hierarchical coarse-to-fine localization using both global descriptors and learned local features
