---
title: "LISA: Reasoning Segmentation via Large Language Model"
authors: Lai, Xin; Tian, Zhuotao; Jiang, Li; et al.
year: 2024
venue: ICCV
topic: vision-language-models
source: "[[raw/vision-language-models/2024/2024-lisa-reasoning-segmentation.pdf]]"
tags: [reasoning-segmentation, implicit-queries, embedding-as-mask, zero-shot-generalization]
---

## Summary

LISA introduces the reasoning segmentation task, requiring models to output segmentation masks for complex, implicit textual queries that demand reasoning beyond explicit object categories. Unlike traditional segmentation relying on explicit instructions or pre-defined categories, LISA enables active reasoning and comprehension of implicit user intention. The model inherits language generation capabilities from multimodal LLMs while producing segmentation masks through an embedding-as-mask paradigm. LISA expands the vocabulary with a special <SEG> token and demonstrates robust zero-shot capability when trained exclusively on reasoning-free datasets. Fine-tuning with just 239 reasoning segmentation samples significantly improves performance, while the authors establish a benchmark with over 1,000 image-instruction-mask samples incorporating complex reasoning and world knowledge.

## Key contributions

- Introduces reasoning segmentation task requiring implicit query understanding and world knowledge integration
- Proposes embedding-as-mask paradigm enabling segmentation output from language models without architectural modification
- Demonstrates strong zero-shot generalization on reasoning tasks despite training on reasoning-free data
- Shows that minimal fine-tuning (239 samples) can substantially improve reasoning segmentation performance

## Method

Language model with special <SEG> token whose embeddings directly encode segmentation information. The embedding-as-mask approach allows seamless integration of segmentation with text generation without requiring separate segmentation heads or architectural modifications.

## Results

Strong performance on reasoning-based segmentation tasks, with particular strength in zero-shot generalization and ability to handle complex implicit queries requiring world knowledge and reasoning.

## Relation to prior work

Extends LLaVA-style vision-language models to dense prediction tasks, introducing reasoning as a key component beyond traditional segmentation. Demonstrates language models' capability for pixel-level prediction tasks.

## Open questions / limitations

Reasoning segmentation benchmark is relatively small (1000 samples); larger-scale benchmarks needed. Embedding-as-mask approach may have limitations for fine-grained spatial prediction. Trade-offs between reasoning capability and segmentation precision not fully explored.

---
