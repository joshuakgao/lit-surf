---
topic: denoising-segmentations
tags: [concept, method]
---

## Definition

Learning from noisy labels (LNL) encompasses techniques designed to train robust models despite imperfect or corrupted annotations. Strategies include noise-aware loss functions, sample reweighting, label correction, noise modeling, and meta-learning approaches. LNL is critical for real-world applications where perfect annotation is expensive or infeasible.

## Origins

Label noise robustness has been extensively studied in image classification. However, [[2025-noisy-annotations-segmentation|Noisy Annotations in Semantic Segmentation]] reveals that existing LNL methods—which primarily target class label noise—fail to adequately handle the spatial inaccuracies introduced in dense prediction tasks like segmentation.

## Key variants / extensions

- **Classification LNL**: Handles semantic label noise through noise transition matrices, symmetric loss functions, meta-learning
- **Segmentation LNL**: Must additionally address spatial noise (boundary perturbations), a unique challenge not well-addressed by classification-focused methods
- **Weak supervision**: Using noisy or incomplete labels (e.g., bounding boxes, scribbles, or weak prompts) as supervision
- **Self-training / Pseudo-labeling**: Using model predictions to refine or correct noisy labels

## Papers using this concept

- [[2025-noisy-annotations-segmentation]] — Demonstrates empirically that standard LNL approaches struggle with spatial label inaccuracies in segmentation
