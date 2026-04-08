---
topic: construction-monitoring
tags: [concept, method]
---

## Definition

Automated identification and analysis of differences between observations of the same scene at different times. Change detection aims to distinguish meaningful changes (object motion, appearance modification, compositional changes) from measurement noise and sensor artifacts. In construction, change detection quantifies progress by identifying completed elements, equipment repositioning, and structural modifications.

## Origins

Classical remote sensing technique for monitoring environmental and urban dynamics using satellite/aerial imagery. Extended to 3D by leveraging point clouds from LiDAR and photogrammetry, enabling geometric analysis without perspective distortion. Three main change detection categories: point-based (direct distance metrics), voxel-based (occupancy grids), and object-based (semantic classification).

## Key variants in construction context

**Point-based change detection**: Direct point-to-point or point-to-surface distance calculations (Cloud2Cloud distance); sensitive to point density variations; useful for fine-grained deformation analysis.

**Voxel-based change detection**: Discretizes 3D space into voxels and detects occupancy changes; handles variable point densities well; implicitly addresses occlusions through occupancy ray tracing; limited by voxel resolution.

**Segment/object-based change detection**: Segments point clouds into objects or regions, detects changes at object level; requires segmentation accuracy; enables semantic interpretation; more robust to noise.

**Semantic-aided change detection**: Combines geometric change (occupancy differences) with semantic change (object class transitions); enables higher-level interpretation; requires segmentation networks.

**Uncertainty-aware change detection**: Models measurement uncertainty and belief functions (Dempster-Shafer theory); distinguishes significant changes from measurement noise; supports rigorous metric tolerance evaluation.

## Related concepts

- [[point-clouds|Point Clouds]] — data source
- [[semantic-segmentation|Semantic Segmentation]] — for object-level interpretation
- [[building-information-model|Building Information Model]] — reference for construction applications
- [[scene-graphs|Scene Graphs]] — semantic representation for predicting changes

## Papers introducing techniques

- [[2024-3d-change-detection-construction-scenarios]] — octree with surface continuity constraints
- [[2023-change-detection-urban-objects-review]] — comprehensive technique survey
- [[2022-change-detection-indoor-construction-bim]] — voxel + uncertainty quantification
- [[2022-semantics-aided-3d-change-detection-construction]] — geometric + semantic fusion

## Current research directions

- Integration of semantics for interpretable change characterization
- Uncertainty quantification through probabilistic frameworks
- Multi-modality fusion (point clouds + imagery + thermal)
- Real-time processing for continuous monitoring
- Transfer learning for cross-site generalization
