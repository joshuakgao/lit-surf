---
title: "SEAGULL: No-reference Image Quality Assessment for Regions of Interest via Vision-Language Instruction Tuning"
authors: Chen, Chen; et al.
year: 2024
venue: arXiv
topic: vision-language-models
source: "[[raw/vision-language-models/2024/2024-seagull-image-quality-assessment-roi.pdf]]"
tags: [image-quality-assessment, region-of-interest, vision-language-instruction, fine-grained-evaluation]
---

## Summary

SEAGULL is a novel vision-language model for fine-grained image quality assessment of regions of interest (ROI), providing region-specific quality guidance crucial for video optimization and image enhancement. While existing IQA methods achieve success analyzing overall image quality, SEAGULL addresses the gap in region-level quality assessment by incorporating a vision-language model guided by segmentation masks (from SAM) and a Mask-based Feature Extractor (MFE) to isolate global and local tokens for specified ROIs. The authors construct SEAGULL-100w with ~100,000 synthetic distortion images containing 33 million ROIs for pre-training, and SEAGULL-3k with ~3,000 authentic distortion ROIs for fine-tuning, enabling accurate fine-grained quality assessment critical for region-specific optimization tasks.

## Key contributions

- First VLM specifically designed for fine-grained region-level image quality assessment
- Introduces Mask-based Feature Extractor for precise ROI quality analysis without losing global context
- Creates large-scale pre-training dataset (SEAGULL-100w) and authentic fine-tuning dataset (SEAGULL-3k) for ROI IQA
- Demonstrates effectiveness on region-level quality assessment for practical applications like video optimization

## Method

Vision-language model with Mask-based Feature Extractor that extracts global and local tokens specifically for ROI regions, using SAM-generated masks to specify regions of interest without modifying overall visual understanding.

## Results

Remarkable performance on fine-grained ROI quality assessment after pre-training on SEAGULL-100w and fine-tuning on SEAGULL-3k, with strong generalization to authentic distortions.

## Relation to prior work

Extends vision-language models into specialized domain of region-level quality assessment, building on instruction-tuning approaches while addressing specific needs of quality-aware applications.

## Open questions / limitations

Approach depends on SAM quality for ROI specification. Synthetic SEAGULL-100w may not fully represent diversity of real-world distortions despite fine-tuning on authentic data. Computational cost of region-specific assessment not thoroughly analyzed.

---
