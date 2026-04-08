---
topic: 3d-scene-understanding
tags: [concept, architecture, encoder, point-cloud]
---

## Definition

**Point cloud encoding** is the process of converting a raw set of 3D points (each with XYZ coordinates and optionally RGB colour, intensity, or learned features) into a compact, fixed-size representation suitable for downstream reasoning. For LLM-based scene understanding, the encoding must map to the LLM's token embedding space via a projector.

## Approaches

**Voxelisation + 3DCNN:** Divides the 3D space into a fixed-resolution grid; aggregates point features per voxel; applies 3D convolutions to extract local and global spatial structure. Computationally efficient and well-suited to regular indoor environments.

**Farthest Point Sampling (FPS) + PointNet++:** Samples a fixed number of representative points; computes hierarchical local features. More flexible for irregular or outdoor point clouds but less efficient for dense indoor scans.

**Feature lifting from 2D (e.g., DINOv2):** Projects 2D image features (from a pre-trained ViT) onto 3D points using known camera poses. Adds rich semantic information beyond raw geometry. SpatialLM ablations show this significantly improves object detection (F1@0.5: 45.0 → 49.4).

## Key findings from SpatialLM ablations

- A learned 3DCNN encoder substantially outperforms random sampling baselines on both layout and object tasks
- DINOv2 feature lifting adds consistent gains, especially for object classification (semantic features complement geometric ones)
- Spatial resolution of K=2 (2.5cm voxels) is optimal — coarser loses detail, finer produces excessively long token sequences that hurt LLM performance
- The Sonata encoder (Point Transformer V3-based) achieves the best results, but the 3DCNN + DINOv2 combination is competitive with lower computational cost

## Papers using this concept

- [[papers/2025-spatiallm-structured-indoor-modeling|SpatialLM (Mao et al., 2025)]] — ablation study across 5 encoder designs for point-cloud-to-LLM projection; 3DCNN + DINOv2 as primary encoder
