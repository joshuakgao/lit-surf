---
topic: world-models
tags: [concept, architecture]
---

## Definition

A Joint Embedding Predictive Architecture (JEPA) is a class of self-supervised models that learn representations by jointly predicting missing parts of sensory input **in representation space** (not pixel space). The model learns both: (1) a meaningful abstract representation, and (2) how to predict future or missing states in that representation.

## Origins

Introduced formally by Yann LeCun and colleagues (LeCun, 2022; Bardes et al., 2024). Builds on predictive coding and masked language modeling (BERT, etc.), but adapted to vision and video. The video variant, V-JEPA, applies this to temporal video prediction.

## Key variants / extensions

- **I-JEPA** (Image JEPA): Learns image representations by predicting masked image regions; used for vision foundation models
- **V-JEPA** (Video JEPA): Predicts masked video frames in representation space; demonstrates emergent physics understanding
- **Comparison to alternatives:**
  - **Pixel-space prediction** (e.g., VideoMAE): Reconstruct pixels directly; less interpretable, slower learning
  - **Contrastive learning** (e.g., SimCLR): Learns via similarity; does not enforce predictive structure
  - **Masked language models** (BERT): Text analogue; JEPA is the vision extension

## Papers using this concept

- [[2025-intuitive-physics-self-supervised-pretraining|Intuitive Physics (V-JEPA)]] — uses masked video inpainting in representation space to learn physics; achieves 96% on violation-of-expectation tasks
