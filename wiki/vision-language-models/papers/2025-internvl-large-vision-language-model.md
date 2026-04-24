---
title: "InternVL: Scaling up Vision Foundation Models and Aligning for Generic Visual-Linguistic Tasks"
authors: [Details in paper]
year: 2024
venue: CVPR
topic: vision-language-models
source: "[[raw/vision-language-models/2025/2025-internvl-large-vision-language-model.pdf]]"
tags: [scaled-vision-foundation, progressive-alignment, multi-stage-training, unified-benchmarks]
---

## Summary

InternVL is a large-scale vision-language foundation model that scales the vision encoder to 6 billion parameters and progressively aligns it with an 8 billion parameter language middleware (QLLaMA) using web-scale image-text data. The architecture comprises InternViT-6B, a customized vision transformer with 6 billion parameters designed for efficiency-performance trade-offs, and QLLaMA, a multilingual-enhanced language middleware that acts as substantial "glue" layer reorganizing visual features. Training proceeds through three progressive stages: vision-language contrastive training leveraging noisy web data, generative training on high-quality captions and VQA, and supervised fine-tuning on multimodal dialogue. InternVL achieves state-of-the-art performance on 32 generic visual-linguistic benchmarks spanning image-level/pixel-level recognition, zero-shot classification and retrieval, and multimodal dialogue, demonstrating broad applicability.

## Key contributions

- Scales vision foundation model to 6 billion parameters while maintaining efficiency
- Introduces progressive three-stage training strategy leveraging diverse data sources from noisy web to high-quality annotations
- Demonstrates state-of-the-art performance on comprehensive set of 32 visual-linguistic benchmarks
- Shows effective integration with LLMs for multimodal dialogue capabilities

## Method

Vision-language foundation model with InternViT-6B vision encoder, QLLaMA language middleware, and three-stage training: contrastive on web-scale data, generative on high-quality datasets, and supervised fine-tuning on dialogue.

## Results

State-of-the-art or competitive performance on 32 benchmarks including visual perception, retrieval, zero-shot classification, and multimodal dialogue tasks, demonstrating broad capability across visual-linguistic domains.

## Relation to prior work

Extends prior vision-language models like CLIP to larger scale and more diverse tasks, showing that scaling and progressive training enables strong performance on comprehensive visual-linguistic task suite.

## Open questions / limitations

Scaling to larger vision models may have diminishing returns or computational limitations. Web-scale training data quality and potential biases not extensively analyzed. Performance gains from 6B vs smaller models not thoroughly compared in efficiency-accuracy trade-offs.
