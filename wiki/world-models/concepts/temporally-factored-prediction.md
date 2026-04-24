---
topic: world-models
tags: [concept, architecture]
---

## Definition

A predictive architecture that decouples appearance (visual features of objects) from dynamics (how appearance changes over time). The model learns to predict future frames by separately modeling what objects look like and how they move, rather than treating visual prediction as a monolithic task.

## Origins

Formally operationalized in [[../papers/2026-babyzwm-zero-shot-world-models|BabyZWM]], though the conceptual idea of factorizing appearance and motion has roots in classical computer vision (e.g., optical flow decomposition, scene flow) and more recent work on disentangled representations.

## Key variants / extensions

- **Sparse temporally-factored prediction** (BabyZWM): Uses masked frame prediction—given frame t and partial frame t+Δt, predict the full frame t+Δt. Sparsity in the mask encourages the model to infer missing appearance from dynamics.
- **Dense prediction**: Full frames visible at each timestep (computationally expensive, less data-efficient).
- **Latent-space factorization**: Some methods factorize in learned representation space rather than pixel space, potentially more efficient but less interpretable.

## Papers using this concept

- [[../papers/2026-babyzwm-zero-shot-world-models|BabyZWM]] — core learning mechanism: sparse masked prediction separates appearance from dynamics naturally

