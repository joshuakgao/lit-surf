---
topic: anomaly-detection
tags: [concept, temporal-analysis, earth-observation]
---

## Definition

Change detection is the task of identifying and localizing temporal differences between two or more images of the same scene captured at different times. Applications span earth observation (deforestation, urban growth, disaster response), surveillance (intrusion detection), robotics (environmental mapping), and autonomous vehicles (obstacle detection).

## Origins

Emerged in remote sensing and earth observation for detecting land cover changes, urban expansion, and natural disasters. Extended to general visual surveillance and scene understanding. Traditional methods used pixel-level differencing or classical computer vision; modern approaches employ deep learning and foundation models.

## Key variants / extensions

- **Pixel-level change detection**: identify individual changed pixels; used in remote sensing
- **Semantic change detection**: identify what changed (e.g., "forest to urban"); requires semantic understanding
- **Open-vocabulary change detection**: describe changes in natural language rather than predefined categories
- **Multi-temporal analysis**: reasoning over sequences of images rather than pairs
- **Temporal consistency**: ensuring consistency regardless of image pair order; critical for practical deployment

## Papers using this concept

- [[papers/2024-towards-generalizable-scene-change-detection|GeSCF (2024)]] — generalizable scene change detection; addresses domain shift and temporal consistency
- [[papers/2025-dynamicearth-open-vocabulary-change-detection|DynamicEarth (2025)]] — open-vocabulary change detection in earth observation; enables natural language querying
