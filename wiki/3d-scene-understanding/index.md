---
topic: 3d-scene-understanding
---

# 3D Scene Understanding — Index

Research on parsing 3D environments — from point clouds, RGBD scans, or video — into structured representations of layout, objects, and spatial relationships. Covers both classical geometry-based methods and LLM-based approaches for indoor scene reconstruction, object detection, and spatial reasoning.

## Papers by year

### 2026
- [[papers/2026-b3seg-camera-free-3dgs-segmentation|B³-Seg: Camera-Free, Training-Free 3DGS Segmentation via Analytic EIG and Beta–Bernoulli Bayesian Updates]] — Bayesian active view selection for 3D Gaussian Splatting segmentation; integrates Grounding DINO + SAM2 + CLIP with Beta–Bernoulli updates; camera-free, training-free, few-second results
<img src="/raw/3d-scene-understanding/2026/thumbnails/2026-b3seg-camera-free-3dgs-segmentation.png" height="300"/>
- [[papers/2026-boxer-lifting-2d-to-3d|Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D]] — Decouples 2D detection from 3D lifting via BoxerNet transformer; fuses multi-view detections with optional depth for metric 3D bounding boxes in open-world scenarios
<img src="/raw/3d-scene-understanding/2026/thumbnails/2026-boxer-lifting-2d-to-3d.png" height="300"/>

### 2025
- [[papers/2025-spatiallm-structured-indoor-modeling|SpatialLM: Training LLMs for Structured Indoor Modeling]] — Encoder-MLP-LLM pipeline that processes point clouds and outputs structured text descriptions of indoor scenes (layout + 3D objects); NeurIPS 2025 SOTA on Structured3D and ScanNet
<img src="/raw/3d-scene-understanding/2025/thumbnails/2025-spatiallm-structured-indoor-modeling.png" height="300"/>

## Concepts

- [[concepts/3d-gaussian-splatting|3D Gaussian Splatting]] — neural rendering via learnable 3D Gaussians; real-time photorealistic rendering without volumetric ray marching; basis for interactive 3D editing and labeling
- [[concepts/active-view-selection|Active View Selection]] — information-theoretic strategy for selecting next observation via Expected Information Gain; greedy (1−1/e) approximation for uncertain 3D tasks
- [[concepts/open-world-detection|Open-World Detection]] — open-vocabulary object detection from arbitrary text/visual prompts without fixed category constraints; enables zero-shot generalization
- [[concepts/3d-bounding-box|3D Bounding Box]] — oriented or axis-aligned boxes in 3D space parameterized by center, dimensions, and rotation; representation for object geometry
- [[concepts/2d-to-3d-lifting|2D-to-3D Lifting]] — predicting metric 3D geometry from 2D image observations and optional depth; decouples 2D localization from 3D geometric prediction
- [[concepts/multi-view-fusion|Multi-View Fusion]] — merging per-frame detections across video or multi-camera rigs via Hungarian matching or online tracking for globally consistent scene-level representations
- [[concepts/structured-scene-representation|Structured Scene Representation]] — encoding 3D scenes as typed parameterised elements; text-as-structure format enabling LLM compatibility and editability
- [[concepts/point-cloud-encoding|Point Cloud Encoding]] — voxelisation, FPS, and DINOv2 feature lifting for mapping raw 3D points into LLM token space; ablation findings on resolution and encoder design

## See also

- [[../vision-language-models/index|Vision-Language Models]] — related: 2D region understanding and localized captioning; overlaps in multimodal LLM architecture patterns
