---
topic: synthetic-datasets
tags: [concept, method]
---

## Definition

Sim-to-real transfer (or domain transfer) refers to training models on synthetic data and evaluating/deploying them on real-world data. The goal is to leverage the advantages of synthetic data (unlimited annotated examples, controlled settings, cost-efficiency) while maintaining performance on real-world distributions that may differ in appearance, lighting, materials, and other factors.

## Origins

Domain adaptation and transfer learning became prominent in computer vision with datasets like ImageNet. The challenge of synthetic-to-real transfer intensified as researchers created photorealistic synthetic datasets (SYNTHIA, GTA V for autonomous driving, etc.).

## Key variants / extensions

- **Direct transfer**: Train on synthetic, test on real without fine-tuning
- **Fine-tuning**: Pre-train on synthetic, fine-tune on limited real data
- **Domain adaptation**: Use techniques to reduce domain gap between synthetic and real
- **Multi-source training**: Combine multiple synthetic datasets to improve robustness

## Papers using this concept

- [[2021-hypersim-photorealistic-synthetic-dataset-indoor-scene]] — Demonstrates strong sim-to-real transfer for semantic segmentation and 3D shape prediction through photorealistic rendering and comprehensive ground truth
