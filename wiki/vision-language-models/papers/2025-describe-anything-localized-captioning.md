---
title: "Describe Anything: Detailed Localized Image and Video Captioning"
authors: Lian, Long; Ding, Yifan; Ge, Yunhao; Liu, Sifei; Mao, Hanzi; Li, Boyi; Pavone, Marco; Liu, Ming-Yu; Darrell, Trevor; Yala, Adam; Cui, Yin
year: 2025
venue: arXiv:2504.16072
affiliations: UC Berkeley, UCSF, NVIDIA
topic: vision-language-models
source: "[[raw/vision-language-models/2025/2025-describe-anything-localized-captioning.pdf]]"
thumbnail: "[[raw/vision-language-models/2025/thumbnails/2025-describe-anything-localized-captioning.png]]"
tags:
  - localized-captioning
  - vision-language
  - ssl
  - dense-captioning
  - video-captioning
---

![](/raw/vision-language-models/2025/thumbnails/2025-describe-anything-localized-captioning.png)

## Summary

Existing Vision-Language Models (VLMs) generate global image captions but struggle to produce detailed, accurate descriptions of *specific regions* — particularly small or occluded objects. Cropping the region of interest (ROI) loses global contextual cues; using the full image loses fine-grained regional detail. This paper introduces the **Describe Anything Model (DAM)**, an architecture that preserves both local detail and global context for detailed localized captioning (DLC) of user-specified regions in both images and videos.

DAM is trained on **DLC-SDP**, a semi-supervised data pipeline that bootstraps high-quality localized caption data from existing segmentation datasets and unlabeled web images. The authors also introduce **DLC-Bench**, an LLM-as-judge benchmark that evaluates detailed localized captions using positive/negative attribute questions rather than reference-based string matching.

DAM achieves state-of-the-art on 7 benchmarks spanning keyword-, phrase-, and detailed-captioning granularities, both in-domain and zero-shot.

## Key contributions

- **Focal prompt**: encodes the ROI at high token density while retaining global image context via cross-attention — the key architectural innovation that resolves the crop-vs-context tradeoff
- **Localized vision backbone**: extends a standard ViT with mask embedding layers and gated cross-attention blocks, allowing local features to attend to global image features without disrupting the pre-trained VLM's sequence length or dimensions
- **DLC-SDP**: a two-stage semi-supervised pipeline that (1) distills high-quality captions from existing annotated datasets using keyword-guided VLM querying, then (2) applies SSL on unlabeled SA-1B images to scale to 1.46M training regions across 819K images
- **DLC-Bench**: LLM-as-judge evaluation on Objects365 validation set using structured positive/negative attribute questions, explicitly designed to penalise hallucinations and reward correct regional detail

## Architecture

**Focal Prompt** takes as input: (1) the full image $I$, (2) the focal crop $I'$ (region expanded by factor $\alpha$, min 48px), and (3) the binary mask $M$. All are passed through the vision encoder. The focal crop uses gated cross-attention adapters in every transformer block to attend to global image features, ensuring contextual grounding without losing local resolution.

**Localized Vision Backbone** adds a mask embedding layer (initialized to zero) before the patch embedding, which takes binary masks as an additional input channel. Gated cross-attention blocks ($\gamma$, $\delta$ learnable, initialized to zero) are inserted into encoder-decoder transformer blocks to allow local features to attend to global features without disrupting the base VLM.

**Video extension**: visual features from all frames are concatenated in the sequence dimension and fed into the LLM. SAM 2 is used to propagate sparse localizations (clicks, scribbles) to masks across frames.

## DLC-SDP Data Pipeline

**Stage 1 — Leveraging Existing Annotations:**
Sources: IVIS, MapillaryVistas v2.0, OpenImages v7, PACO (~622K regions). For each mask-referred region, the pipeline queries a VLM for class name + keywords (object parts, name, entities), then expands each keyword into a detailed caption via VLM. An LLM summarizes to multi-sentence descriptions. Filtering with confidence-based SSL keeps only high-quality samples.

**Stage 2 — SSL on Unlabeled Images:**
Uses OWL-ViT2 + Cascade Mask R-CNN to detect/segment objects in SA-1B (10% subset, ~592K images). SSL with DAM initialized from Stage 1 generates pseudo-labels; high-confidence samples (top 10%) are added to training. Total: 1.46M regions, 819K images.

## Results

- **IVIS (open-class keyword)**: 72.8 Pos% / 61.3 Neg% (vs GPT-4o: 5.0/72.9; VP-SPHINX: 23.4/50.6)
- **PACO (phrase-level)**: 83.0 Pos% / 67.3 Neg% (vs GPT-4o: 42.4/65.4)
- **DLC-Bench (detailed, zero-shot)**: 82.2 Pos% / 67.3 Neg% — SOTA among all tested models
- **HC-STVG (video DLC)**: 39.8% relative improvement over previous best
- Ablations confirm focal prompt (+5.2% on DLC-Bench positive) and cross-attention (+3.7%) are both critical; prompt augmentation slightly degrades benchmark performance so is excluded by default

## Relation to prior work

- **GPT-4o / VP-SPHINX**: Prior SOTA on localized captioning benchmarks. DAM substantially outperforms both, especially on detailed granularity tasks. VP-SPHINX excels at keyword tasks but produces vague descriptions at phrase/detailed level.
- **Region-referring VLMs** (SoM, RegionGPT, CogVLM, etc.): Prior work encodes region via referring tokens or bounding boxes overlaid on images; DAM's focal prompt is architecturally distinct — it encodes the mask as a separate 2D input rather than a visual marker.
- **VideoRefer-700k**: Concurrent video DLC work; DAM surpasses it on HC-STVG despite VideoRefer sourcing data from Panda-70M.

## Open questions / limitations

- The DLC-SDP pipeline relies on existing segmentation datasets for Stage 1, which are predominantly object-centric — broader scene-level or stuff-class regions are underrepresented
- Focal prompt requires the mask as input; for downstream applications where masks aren't available, a detect-then-caption pipeline is needed
- DLC-Bench is evaluated only on Objects365 — coverage of non-object regions (backgrounds, textures, scenes) is limited
- Hallucination on fine-grained motion/appearance details in video remains a failure mode when camera motion is complex
