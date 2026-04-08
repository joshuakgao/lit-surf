---
topic: vision-language-models
tags: [concept, architecture, localized-captioning]
---

## Definition

A **focal prompt** is an input representation for VLMs that encodes a region of interest (ROI) at high token density while preserving global image context through cross-attention. It resolves the fundamental tension in localized captioning between cropping (high local detail, lost global context) and full-image encoding (global context, poor local resolution for small regions).

## Origins

Introduced in DAM (Describe Anything Model) by Lian et al., 2025. Motivated by the observation that prior VLMs either crop the ROI (losing context) or overlay masks/boxes on the full image (losing local token density for small objects).

## How it works

Given a region mask $M$, the focal prompt constructs three inputs:
1. **Full image** $I$ — provides global context
2. **Focal crop** $I'$ — the ROI expanded by factor $\alpha$ (default $\alpha=3$, min 48px in each dimension) to include surrounding context
3. **Binary mask** $M$ — passed to the localized vision backbone's mask embedding layer

The full image and focal crop are both encoded by the vision encoder. Gated cross-attention adapters inserted into each transformer block allow the focal crop's local features to attend to the full image's global features. The resulting visual tokens are fed into the LLM along with a text prompt.

The cross-attention gates ($\gamma$, $\delta$) are initialized to zero so the pre-trained VLM's behavior is unchanged at init; the model learns to selectively incorporate global context during fine-tuning.

## Key properties

- Does not change the sequence length seen by the LLM — parameter and memory overhead is minimal
- Works for any localization type: clicks, scribbles, boxes, masks, polygons (all converted to masks via SAM 2)
- Extends naturally to video by concatenating frame features in the sequence dimension

## Papers using this concept

- [[papers/2025-describe-anything-localized-captioning|Describe Anything (Lian et al., 2025)]] — introduced the concept; SOTA on 7 DLC benchmarks
