---
topic: denoising-segmentations
tags: [concept, term]
---

## Definition

Label noise refers to incorrect or inaccurate annotations in training data. In segmentation, this includes class label errors (assigning the wrong semantic category), boundary errors (misaligned or imprecise masks), and missing annotations (instances that should be labeled but are not). Label noise can stem from human annotation errors or mistakes by automated labeling tools.

## Origins

Label noise has been extensively studied in image classification, but instance segmentation introduces unique spatial prediction challenges. [[2025-noisy-annotations-segmentation|Noisy Annotations in Semantic Segmentation]] systematically characterizes noise patterns in dense prediction tasks, showing that segmentation is far more sensitive to spatial inaccuracies than classification.

## Key variants / extensions

- **Spatial noise**: Boundary shifts, shrinkage, or expansion of masks (unique to segmentation)
- **Semantic noise**: Incorrect class labels applied to objects
- **Instance noise**: Missing objects or false-positive annotations
- **Weak annotation noise**: Errors introduced by foundation models (e.g., SAM) when given imprecise prompts

## Papers using this concept

- [[2025-noisy-annotations-segmentation]] — Characterizes annotation noise types and their effects on segmentation robustness
