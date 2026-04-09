---
topic: 3d-scene-understanding
tags: [concept, method]
---

## Definition

Open-world or open-vocabulary object detection refers to the ability to detect and classify objects belonging to categories not seen during training. Rather than being constrained to a fixed set of object classes, these models accept arbitrary text descriptions or visual prompts at inference time and can locate instances of those objects in images or video.

## Origins

Emerged from vision-language models (CLIP, ALIGN) that learned joint text-image embeddings. Early work (Minderer et al., OWLv1/OWLv2) adapted this to region-level detection via open-vocabulary image-text alignment.

## Key variants / extensions

- **OWLv2** (Minderer et al., 2023): Vision Transformer-based open-vocabulary 2D detector using prompt embeddings (text or visual examples)
- **BoxerNet** (DeTone et al., 2026): Extends open-vocabulary 2D detection to 3D by lifting detections to oriented bounding boxes with geometric reasoning
- **Region-level alignment**: Cropping detected regions and independently assessing them against text prompts improves robustness over full-image alignment

## Papers using this concept

- [[2026-boxer-lifting-2d-to-3d|Boxer]] — uses OWLv2 to find arbitrary objects in video, then lifts to 3D without category-specific training
- [[2025-spatiallm-structured-indoor-modeling|SpatialLM]] — extends open-vocabulary understanding to structured scene description (not just detection)
