---
title: Towards Fine-Grained Video Question Answering
authors: Dai, Wei; Luo, Alan; Durante, Zane; Dash, Debadutta; Milstein, Arnold; Schulman, Kevin; Adeli, Ehsan; Fei-Fei, Li
year: 2025
venue: arXiv:2503.06820
affiliations: Stanford University
topic: video-understanding
source: "[[raw/video-understanding/2025/2025-moma-qa-fine-grained-video-question-answering.pdf]]"
thumbnail: "[[raw/video-understanding/2025/thumbnails/2025-moma-qa-fine-grained-video-question-answering.png]]"
tags:
  - video-qa
  - scene-graph
  - temporal-grounding
  - benchmark
  - vlm
  - fine-grained
  - multi-actor
---

![](/raw/video-understanding/2025/thumbnails/2025-moma-qa-fine-grained-video-question-answering.png)

## Summary

Existing VideoQA datasets lack fine-grained temporal and spatial annotations — models can answer questions by pattern-matching without genuine temporal localisation or entity-level spatial reasoning. This paper addresses both gaps with two contributions: (1) **MOMA-QA**, a new benchmark derived from the MOMA (Multi-Object Multi-Actor) dataset featuring 300K+ QA pairs with ground-truth temporal intervals and bounding box augmentations, and (2) **SGVLM** (Scene Graph Video Language Model), a video-language model that integrates a frame encoder, a scene graph predictor, and an efficient frame localizer for fine-grained spatiotemporal video QA.

SGVLM achieves SOTA on MOMA-QA in both zero-shot and fine-tuned settings, and competitive performance on NExT-QA, while also performing strongly on moment retrieval and highlight detection tasks.

## Key contributions

- **MOMA-QA dataset**: 300,791 QA pairs across 3 question types (relationship, motion, description) with ground-truth temporal interval annotations and bounding box augmentations — specifically designed to require temporal localisation and spatial entity reasoning
- **SGVLM architecture**: integrates a scene graph predictor into the video-language pipeline, enabling explicit spatial relationship understanding alongside temporal localisation
- **Frame localizer with self-attention masking**: restricts frame and scene graph tokens to attend only to question tokens, improving question-relevance of selected frames and boosting moment retrieval performance
- **Bounding box augmentations**: a technique that zooms into entity-centric regions of video frames to reduce ambiguity in multi-actor scenes, improving entity-specific reasoning

## Dataset: MOMA-QA

**Sources:** MOMA dataset (147 actors, 308 activities, 1,412 raw videos)
**Scale:** 300,791 QA pairs; 27,586 questions from NExT-QA training split for fine-tuning
**Question types:**

| Type | Format | Focus |
|------|--------|-------|
| Relationship | When $[C_s]$ is $[V_i]$, what is $[C_t]$ $[E_{st}]$? | Spatial/entity relationships between actors |
| Motion | When $[C_s]$ is $[V_i]$, how many $[identity]$ are in scene? | Counting/motion in temporal context |
| Description | When $[C_s]$ is $[V_i]$, how many $[identity]$ are in scene? | Describing sub-activity details |

Each question grounded to temporal interval $[t_{start}, t_{end}]$ and sub-activity description $C_i$. **Bounding box augmentations** crop frames to the queried entity to minimise multi-actor ambiguity.

**Comparison to prior datasets:** MOMA-QA is one of the largest open-ended VideoQA benchmarks (300K pairs vs. NExT-QA 47K, ActivityNet-QA 58K) and is unique in combining temporal grounding annotations, bounding box annotations, and scene graph structure.

## Architecture: SGVLM

**Frame Encoder:** ViT-based (304M parameters); produces patch image features and a context feature vector **f**

**Scene Graph Predictor:** Neural Motifs backbone pre-trained on Visual Genome and fine-tuned on MOMA-QA. Predicts bounding boxes $B$, object classes $O$, and image features; a label probability vector $\mathbf{p}_b$ is included for each box. Scene graph features encoded via Q-Former + LLM into scene graph token embeddings $\mathbf{S}$.

**Frame Localizer:** Based on VTG architecture; uses hybrid alignment + contrastive learning. A **self-attention mask** in the transformer encoder restricts frame and scene graph tokens to interact only with question tokens (not with each other), focusing attention on question-relevant content. The localizer selects top-$k$ frames ranked by salience score $s_i$.

**LLM:** Processes concatenated frame tokens $\mathbf{X}_v$ and scene graph tokens $\mathbf{X}_s$ together with question tokens $\mathbf{Q}$ to generate the final answer.

**Loss:** Combined format reward + contrastive learning (intra-video: cosine similarity between frame and query embeddings; inter-video: negative samples from other videos in the batch) + cross-entropy on answer token prediction.

## Results

**Zero-shot MOMA-QA:**

| Model | Accuracy | WUPS@0.9 |
|-------|----------|----------|
| InternVideo | 50.00 | 0.1036 |
| mPLUG-2 | 53.19 | 0.2081 |
| BLIP-2 | 50.00 | 0.0000 |
| SeViLa | 51.22 | 0.2277 |
| **SGVLM** | **58.69** | **0.3283** |

**Fine-tuned MOMA-QA:**

| Model | Accuracy | WUPS@0.9 |
|-------|----------|----------|
| SeViLa | 63.42 | 0.6064 |
| **SGVLM** | **66.64** | **0.6643** |

**NExT-QA (fine-tuned):**

| Type | SGVLM | SeViLa |
|------|-------|--------|
| Causal | 75.2 | 67.01 |
| Temporal | 66.3 | 65.51 |
| Descriptive | 83.4 | 79.25 |
| **Average** | **74.3** | **74.3** |

**Moment Retrieval & Highlight Detection (MOMA-QA):** R1@0.5 44.65, mAP 46.06 — ranks second overall, leads in HD IoU>Very Good threshold. Attention mask ablation confirms +0.97% advantage on mAP@0.5.

## Relation to prior work

- **SeViLa** (Yu et al., 2023): prior SOTA on VideoQA with frame localiser; SGVLM surpasses it by 3.04% on MOMA-QA fine-tuned accuracy and substantially on zero-shot metrics by integrating scene graphs
- **TimeSearch-R** ([[papers/2025-timesearch-r-temporal-search-video-understanding|Pan et al., 2025]]): both papers address temporal frame selection for VideoQA, but from different angles — TimeSearch-R uses RL to learn adaptive search; SGVLM uses a supervised localizer with scene graph context. Complementary approaches.
- **VTG-LLM / Q-Former**: SGVLM's frame localizer and scene graph encoder are based on these components; SGVLM's contribution is their integration with explicit scene graph prediction

## Open questions / limitations

- MOMA-QA is derived from a controlled activity dataset; generalisability to in-the-wild videos with diverse scenes and actors is untested
- Scene graph predictor requires pre-training on Visual Genome and fine-tuning on annotated data — not zero-shot generalisable to new object categories
- Bounding box augmentations require object detection annotations at inference; this dependency limits deployment in unannotated settings
- NExT-QA improvement over SeViLa is marginal overall (74.3% vs 74.3%) — scene graphs primarily help relationship and description questions, less so temporal reasoning
