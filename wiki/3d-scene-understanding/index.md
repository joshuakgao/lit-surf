---
topic: 3d-scene-understanding
---

# 3D Scene Understanding — Index

Research on parsing 3D environments — from point clouds, RGBD scans, or video — into structured representations of layout, objects, and spatial relationships. Covers both classical geometry-based methods and LLM-based approaches for indoor scene reconstruction, object detection, and spatial reasoning.

## Papers by year

### 2025
- [[papers/2025-spatiallm-structured-indoor-modeling|SpatialLM: Training LLMs for Structured Indoor Modeling]] — Encoder-MLP-LLM pipeline that processes point clouds and outputs structured text descriptions of indoor scenes (layout + 3D objects); NeurIPS 2025 SOTA on Structured3D and ScanNet
<img src="../../raw/3d-scene-understanding/2025/thumbnails/2025-spatiallm-structured-indoor-modeling.png" height="300"/>

## Concepts

- [[concepts/structured-scene-representation|Structured Scene Representation]] — encoding 3D scenes as typed parameterised elements; text-as-structure format enabling LLM compatibility and editability
- [[concepts/point-cloud-encoding|Point Cloud Encoding]] — voxelisation, FPS, and DINOv2 feature lifting for mapping raw 3D points into LLM token space; ablation findings on resolution and encoder design

## See also

- [[../vision-language-models/index|Vision-Language Models]] — related: 2D region understanding and localized captioning; overlaps in multimodal LLM architecture patterns
