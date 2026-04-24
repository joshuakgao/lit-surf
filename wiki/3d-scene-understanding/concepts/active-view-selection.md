---
topic: 3d-scene-understanding
tags: [concept, method]
---

## Definition

Active view selection is a strategy for choosing the next informative observation (e.g., camera viewpoint, sensor pose) to maximize information gain about an unknown target. Rather than using a fixed or random set of views, the method computes a utility score for candidate views—typically Expected Information Gain (EIG)—and greedily selects the view that would reduce posterior uncertainty most. This approach is particularly valuable in interactive 3D tasks (segmentation, reconstruction, annotation) where compute is limited and human or model time is costly.

## Origins

Active learning and information-theoretic view selection have long histories in robotics, computer vision, and experimental design. Expected Information Gain derives from information theory (Shannon entropy, mutual information). In 3D understanding, active view selection has been applied to model uncertainty in depth estimation, 3D reconstruction, and more recently (B³-Seg, 2026) to Bayesian 3D labeling of neural scene representations.

## Key variants / extensions

- **Expected Information Gain (EIG)**: Compute the expected reduction in entropy/uncertainty if a view were selected; greedy EIG selection achieves (1−1/e) approximation to optimal submodular selection.
- **Variance reduction**: Select views that would most reduce posterior variance or confidence intervals on target quantities.
- **Query entropy**: Select views where model predictions have highest entropy (uncertainty sampling).
- **Diversity-based**: Select views that are maximally different from previously observed views, reducing spatial clustering.
- **Cost-aware selection**: Balance information gain against view acquisition cost (e.g., robot movement, human annotation effort).

## Papers using this concept

- [[2026-b3seg-camera-free-3dgs-segmentation]] — uses analytic EIG to greedily select views for Bayesian 3DGS segmentation; derives (1−1/e) greedy approximation guarantees
