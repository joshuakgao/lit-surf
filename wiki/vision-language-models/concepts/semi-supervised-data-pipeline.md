---
topic: vision-language-models
tags: [concept, method, data, ssl]
---

## Definition

A **semi-supervised data pipeline** for VLM training combines a small set of human-annotated or existing high-quality labeled data with a large pool of unlabeled data, using the model's own predictions as pseudo-labels to iteratively expand the training set. In the context of localized captioning, this addresses the fundamental bottleneck that high-quality region-level captions are expensive to collect at scale.

## Origins in DLC-SDP

The DLC-SDP pipeline (Lian et al., 2025) is a concrete instantiation for detailed localized captioning, operating in two stages:

**Stage 1 — Distillation from Existing Annotations:**
Leverages existing segmentation datasets (IVIS, MapillaryVistas, OpenImages, PACO) with ~622K annotated regions. For each mask, an off-the-shelf VLM is queried with region-specific keywords (object class, parts, entities) to generate detailed descriptions. An LLM then summarizes these into multi-sentence captions. Confidence-based filtering retains only high-quality outputs.

**Stage 2 — SSL on Unlabeled Images:**
Applies the Stage 1 model to unlabeled SA-1B images (10% subset, ~592K images). OWL-ViT2 + Cascade Mask R-CNN detect and segment objects; the model generates pseudo-label captions; the top 10% by confidence score are added to training. Final dataset: 1.46M regions across 819K images.

## Key design choices

- Confidence filtering at each stage is critical — without it, noisy pseudo-labels degrade performance
- Using SSL with 10% of SA-1B improves DLC-Bench accuracy to 67.3% (vs 63.8% without); further scaling with more unlabeled data is expected to improve further
- The pipeline is fully automated and does not require human annotators beyond what existed in the source datasets

## Broader context

This approach is consistent with the trend across vision-language research of bootstrapping large-scale training data via:
- Knowledge distillation from larger/stronger models (BLIP-2, LLaVA)
- Self-training with confidence filtering (common in semi-supervised classification)
- Leveraging existing structured annotations rather than collecting from scratch

## Papers using this concept

- [[papers/2025-describe-anything-localized-captioning|Describe Anything (Lian et al., 2025)]] — DLC-SDP; 1.46M high-quality region captions generated without human annotation
