---
topic: depth-estimation
tags: [concept, method/annotation]
---

## Definition

Pseudo-labeling is the automatic generation of labels for unlabeled data using a pre-trained model. In depth estimation, a well-trained teacher model forwards unlabeled images to produce dense depth predictions, which serve as training targets for a student model. The quality of pseudo-labels directly depends on teacher accuracy and the diversity of unlabeled data.

## Origins

Pseudo-labeling has been used in semi-supervised learning for decades. For depth estimation, [[2024-depth-anything]] demonstrates practical pseudo-labeling at massive scale: using a teacher trained on 1.5M labeled images to annotate 62M unlabeled images. The work reveals that pseudo-label quality is sufficient for learning when combined with strong data augmentations that force the student to develop robust features rather than memorizing teacher predictions.

## Key variants / extensions

- **Single-stage pseudo-labeling**: Teacher generates labels once; student trains on labeled + pseudo-labeled mix
- **Iterative pseudo-labeling**: Retrain teacher on student predictions, repeating the cycle
- **Quality filtering**: Select only high-confidence pseudo-labels (e.g., via entropy or confidence thresholds)
- **Noise-robust losses**: Use affine-invariant loss or other robust objectives designed for imperfect pseudo-labels
- **Multi-source pseudo-labels**: Ensemble predictions from multiple teachers or models

## Papers using this concept

- [[2024-depth-anything]] — Leverages teacher model to automatically annotate 62M unlabeled images; shows that pseudo-labels improve generalization when student is trained with strong perturbations
