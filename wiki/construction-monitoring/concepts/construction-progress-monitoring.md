---
topic: construction-monitoring
tags: [concept, application]
---

## Definition

Automated systems for tracking and documenting the progression of construction work through time, comparing as-built state against as-planned BIM, identifying completed tasks, measuring percentage completion, and detecting deviations or delays. Construction progress monitoring enables project management, schedule adherence tracking, quality control, and safety assurance by providing continuous, objective assessment of work completion.

## Origins

Emerged from need to automate tedious visual inspections and manual surveys in Architecture-Engineering-Construction (AEC) industry. Early approaches relied on time-consuming professional surveys using total stations and leveling devices. Adoption of 3D laser scanning (LiDAR, TLS) and UAV-based photogrammetry provided fast, objective data for automated analysis. Building Information Modeling (BIM) provided standardized as-planned reference geometry enabling systematic comparison.

## Key techniques

- **TLS (Terrestrial Laser Scanning)**: High-resolution point cloud acquisition from ground-based scanners; excellent for indoor and confined spaces
- **ALS/MLS (Airborne/Mobile Laser Scanning)**: Large-scale outdoor acquisition from planes or vehicles
- **UAV Photogrammetry**: Drone-based image acquisition with SfM reconstruction; practical for site accessibility
- **BIM comparison**: As-built point clouds compared against as-planned BIM geometry to identify completions, deviations, or quality issues
- **Occupancy-based change detection**: Voxel/occupancy grid analysis to identify spatial differences between epochs
- **Semantic-aided analysis**: Combining geometric change detection with object-level semantic understanding for higher-level progress interpretation

## Related concepts

- [[point-clouds|Point Clouds]] — data source for progress monitoring
- [[building-information-model|Building Information Model (BIM)]] — reference geometry for as-built vs. as-planned comparison
- [[change-detection|Change Detection]] — core technique for identifying progress
- [[semantic-segmentation|Semantic Segmentation]] — enabling object-level interpretation of changes

## Papers using this concept

- [[2024-3d-change-detection-construction-scenarios]] — semantic change types for construction progress
- [[2023-change-detection-urban-objects-review]] — comprehensive review including construction applications
- [[2022-change-detection-indoor-construction-bim]] — BIM-based progress verification with uncertainty
- [[2022-semantics-aided-3d-change-detection-construction]] — geometric and semantic analysis for progress

## Open challenges

- Scaling to multi-year, multi-phase projects with frequent scene occlusions
- Distinguishing permanent construction progress from temporary equipment/materials
- Handling complex indoor environments with limited scanning views
- Real-time or near-real-time processing for continuous monitoring
- Bridging semantic gap between raw point clouds and high-level project progress metrics
