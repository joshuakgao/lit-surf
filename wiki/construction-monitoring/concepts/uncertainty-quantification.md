---
topic: construction-monitoring
tags: [concept, method]
---

## Definition

Rigorous assessment and propagation of measurement uncertainty, sensor stochastic properties, and data incompleteness through analysis pipelines to produce confidence estimates for detected changes. Rather than treating point clouds as deterministic, uncertainty quantification models belief functions and confidence levels, enabling distinction between significant changes and measurement artifacts.

## Origins

Classical statistical approach in metrology and surveying for understanding measurement error sources. Extended to 3D point cloud analysis by explicitly modeling sensor uncertainty in registration, occupancy estimation, and change detection. Dempster-Shafer theory of evidence provides framework for combining multiple uncertain evidence sources.

## Key techniques in construction context

**Measurement uncertainty modeling**:
- LiDAR range measurement uncertainty depends on distance, angle, surface material
- Photogrammetry uncertainty depends on camera calibration, image matching quality, triangulation geometry
- Stochastic error models capture systematic and random components

**Belief functions and evidence theory (Dempster-Shafer)**:
- Represent uncertainty in occupancy estimates as belief mass assignments
- Combine evidence from multiple measurements using Dempster's combination rule
- Support reasoning with incomplete information and conflicting evidence
- Enable quantification of plausible intervals for changes

**Level of Accuracy (LOA) thresholding**:
- BIM specifies expected geometric accuracy (e.g., LOA 40 = ±50mm)
- Uncertainty quantification determines whether detected differences exceed LOA or are noise
- Avoids false positives from measurement error and registration imperfection

**Occlusion and incompleteness**:
- Point clouds incomplete due to occlusions, sensor limitations, access constraints
- Uncertainty modeling accounts for missing information in occupancy reasoning
- Ray-based methods trace sensor viewing rays to reason about visibility

## Related concepts

- [[change-detection|Change Detection]] — primary application of uncertainty quantification
- [[point-clouds|Point Clouds]] — source of uncertainty
- [[building-information-model|Building Information Model]] — LOA specification for tolerance

## Papers emphasizing uncertainty

- [[2022-change-detection-indoor-construction-bim]] — Dempster-Shafer theory for change detection with uncertainty
- [[2022-semantics-aided-3d-change-detection-construction]] — uncertainty in semantic change estimates

## Current research needs

- Propagating uncertainty through multi-stage pipelines (registration → occupancy → change detection)
- Learning uncertainty models for deep learning-based change detection
- Efficient uncertainty computation for large-scale point clouds
- Communicating uncertainty to practitioners in actionable terms (confidence scores, confidence intervals)
- Balancing computational cost of rigorous uncertainty quantification vs. practical real-time requirements
