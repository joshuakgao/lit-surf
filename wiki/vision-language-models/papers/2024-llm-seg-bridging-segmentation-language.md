---
title: "LLM-Seg: Bridging Image Segmentation and Large Language Model Reasoning"
authors: Wang, Junchi; Ke, Lei; et al.
year: 2024
venue: CVPR Workshop
topic: vision-language-models
source: "[[raw/vision-language-models/2024/2024-llm-seg-bridging-segmentation.pdf]]"
tags: [reasoning-segmentation, sam-integration, mask-proposal-selection, dataset-generation]
---

## Summary

LLM-Seg introduces reasoning segmentation, a task where segmentation systems reason about implicit user intention through LLM reasoning before generating target segmentation masks. The framework effectively connects the Segment Anything Model (SAM) with LLMs through intelligent mask proposal selection, leveraging LLM reasoning to identify which of SAM's proposals correspond to the user's intent. The authors propose an automatic data generation pipeline and construct LLM-Seg40K, a new reasoning segmentation dataset. The approach demonstrates competitive performance with existing methods and shows the proposed pipeline can efficiently produce high-quality reasoning segmentation datasets, establishing LLM-Seg40K as a benchmark for training and evaluating reasoning segmentation approaches.

## Key contributions

- Introduces reasoning segmentation combining SAM's mask generation with LLM reasoning for implicit query understanding
- Proposes efficient mask proposal selection mechanism bridging segmentation models and language reasoning
- Creates automatic data generation pipeline and LLM-Seg40K benchmark for reasoning segmentation
- Demonstrates competitive performance while efficiently generating high-quality training data

## Method

Two-stage pipeline: (1) SAM generates multiple mask proposals, (2) LLM reasons about implicit queries and selects appropriate proposals through cross-modal reasoning about textual descriptions and visual content.

## Results

Competitive performance on reasoning segmentation tasks, with efficient data generation pipeline capable of producing high-quality datasets for further research.

## Relation to prior work

Similar motivation to LISA's reasoning segmentation but uses explicit mask proposal mechanism (SAM) rather than embedding-as-mask approach. Shows complementary approach to dense prediction with reasoning.

## Open questions / limitations

Approach depends on SAM's proposal quality which may vary across scenarios. LLM-Seg40K dataset, while useful, is relatively small compared to other vision-language datasets. Efficiency of mask selection vs. full end-to-end approaches not thoroughly compared.

---
