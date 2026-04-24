---
topic: point-cloud-registration
tags: [concept, method]
---

## Definition

Geometric consistency refers to spatial constraints that enforce coherence in point correspondences across two point clouds. Rather than matching individual points in isolation, geometric consistency ensures that matched points preserve local spatial relationships—distances, angles, and neighborhood structure. This is particularly valuable in ambiguous scenarios (low-overlap, symmetric regions) where point-to-point distance alone is unreliable.

## Origins

Fundamental principle in traditional registration methods (ICP variants) that enforces spatial coherence through energy minimization. In modern learning-based approaches, geometric constraints are explicitly encoded into feature representations. [[papers/2023-geotransformer|GeoTransformer]] encodes pairwise distances and triplet-wise angles as rotation-invariant features.

## Key variants / extensions

- **Pairwise distance encoding**: Invariant to rotation; captures relative positioning between point pairs
- **Triplet-wise angle encoding**: Invariant to rigid transformations; captures local geometric structure through 3-point angles
- **Spatial consistency losses**: Training objectives that penalize geometrically inconsistent matches
- **Graph-based consistency**: Enforcing consistency through edge and cycle constraints in correspondence graphs

## Papers using this concept

- [[papers/2023-geotransformer|GeoTransformer (2023)]] — Encodes pairwise distances and angles in transformer; improves inlier ratio from 22.7% to 94.5% through explicit geometric invariance
