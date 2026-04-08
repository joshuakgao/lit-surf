---
topic: visual-localization
tags: [concept, method]
---

## Definition

Learned features are image descriptors extracted by convolutional neural networks, replacing hand-crafted features (SIFT, SURF, ORB) for image matching and localization. Learned features include both sparse keypoint detectors (identifying salient locations) and dense or sparse descriptors (representing those locations). They leverage CNN representations to capture semantic and geometric patterns invariant to appearance changes.

## Origins

SuperPoint (2018) pioneered self-supervised learning of sparse keypoints and descriptors. DELF (2017) used attention mechanisms for landmark detection. Learned features have since become standard in visual localization and structure-from-motion.

## Key variants / extensions

- **Sparse vs. dense**: Sparse learned features (keypoints + descriptors) vs. dense pixel-level features
- **Self-supervised learning**: SuperPoint uses synthetic data augmentation for unsupervised training
- **Attention-based detection**: DELF uses attention to weight keypoint importance
- **Local vs. global features**: Local features capture fine geometric details; global features capture scene-wide context
- **Joint prediction**: Simultaneously predicting keypoints and descriptors in a single network

## Papers using this concept

- [[2019-hierarchical-localization-at-large-scale]] — Combines learned local features with global CNN descriptors for robust hierarchical localization
