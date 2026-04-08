---
topic: image-inpainting
tags: [concept, method]
---

## Definition

Multimodal guidance in inpainting refers to using multiple complementary information sources (text, spatial masks, reference images, color strokes) to control the inpainting process. Different modalities serve distinct purposes: semantic modalities (text, exemplars) specify what content to generate; spatial modalities (masks, strokes) specify where and how to place it. Unified frameworks combine these modalities through appropriate conditioning mechanisms (cross-attention for semantic, image blending for spatial).

## Origins

Early work used single modalities (text, masks, exemplars). [[2022-smartbrush-text-shape-guided-inpainting|SmartBrush]] pioneered simultaneous text+shape guidance. [[2023-unipaint-multimodal-inpainting|Uni-paint]] generalized to arbitrary combinations of unconditional, text, stroke, exemplar, and mixed modes.

## Key variants / extensions

- **Semantic modalities**: Text descriptions, exemplar images, semantic masks
- **Spatial modalities**: Mask shapes, color strokes, bounding boxes
- **Precision control**: Variable strictness of spatial constraint adherence
- **Mode combination**: Flexible mixing of multiple modalities simultaneously

## Papers using this concept

- [[2022-smartbrush-text-shape-guided-inpainting]] — Combines text and shape with precision-controlled masks
- [[2023-unipaint-multimodal-inpainting]] — First unified framework supporting unconditional, text, stroke, exemplar, and mixed modes
- [[2025-corrfill-reference-based-inpainting]] — Combines reference image with correspondence constraints
