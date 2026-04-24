---
topic: depth-estimation
tags: [concept, method/semi-supervised-learning]
---

## Definition

Self-training is a semi-supervised learning technique where a model trained on labeled data (teacher) generates pseudo-labels for unlabeled data. A new model (student) is trained on the combination of labeled and pseudo-labeled data, potentially iterating this process. The technique is particularly relevant for depth estimation where manual annotation is expensive but model-predicted depth maps are dense and interpretable.

## Origins

Self-training has roots in early semi-supervised learning (Nigam et al., 2000s). In depth estimation, [[2024-depth-anything]] demonstrated its effectiveness at scale with 62M unlabeled images, but revealed a critical limitation: naive self-training fails when sufficient labeled data already exists (teacher and student make similar errors). The key breakthrough was showing that strong data augmentations force learning of robust representations that generalize better.

## Key variants / extensions

- **Naive self-training**: Directly train student on pseudo-labeled data; fails without careful perturbations
- **Augmentation-driven self-training**: Add strong color distortions and spatial mixing (CutMix) to challenge the student
- **Multi-stage self-training**: Iterate teacher→pseudo-labeling→student cycles
- **Semantic-aware self-training**: Combine pseudo-labels with auxiliary semantic signals to combat label noise
- **Iterative self-training**: Retrain teacher on student-labeled data in later iterations

## Papers using this concept

- [[2024-depth-anything]] — Shows naive self-training fails on depth when labeled data is sufficient; strong perturbations (color jitter, Gaussian blur, CutMix) unlock benefits of 62M unlabeled images
