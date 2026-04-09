---
title: "Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D"
authors: DeTone, Shen, Zhang, Ma, Straub, Newcombe, Engel
year: 2026
venue: Meta Reality Labs Research
topic: 3d-scene-understanding
source: "[[raw/3d-scene-understanding/2026/2026-boxer-lifting-2d-to-3d.md]]"
thumbnail: "[[raw/3d-scene-understanding/2026/thumbnails/2026-boxer-lifting-2d-to-3d.png]]"
tags: [3d-detection, open-vocabulary, object-detection]
---

![](/raw/3d-scene-understanding/2026/thumbnails/2026-boxer-lifting-2d-to-3d.png)

## Summary

Boxer addresses open-world 3D object detection in indoor scenes by lifting 2D bounding box detections to 3D oriented bounding boxes (OBBs). The approach combines an open-vocabulary 2D detector (OWLv2) with BoxerNet, a learned module that leverages camera intrinsics, gravity direction, and optional depth to infer full 3D geometry from image crops. Detections across multiple frames are fused via Hungarian matching or online tracking to produce globally consistent scene-level 3D detections. The system is evaluated on multiple data sources (Aria, ScanNet, SUN-RGBD, CA-1M) and demonstrates practical deployment capabilities without requiring 3D annotations during training.

## Key contributions

- **Open-world 2D-to-3D lifting**: Uses OWLv2 to find arbitrary objects from text/visual prompts, then lifts to 3D without category-specific training
- **BoxerNet design**: DINOv3 image encoding + cross-attention over camera and depth features predicts full 3D OBB parameters per detection
- **Multi-view temporal fusion**: Hungarian-algorithm-based offline fusion and online tracking for scene-level consistency across frames
- **Multi-source compatibility**: Single pipeline works with diverse inputs (fisheye cameras, RGB-D sequences, monocular video with SLAM)

## Method

**2D Detection**: OWLv2 open-vocabulary detector finds objects in each frame using text prompts or manual 2D bounding box annotations. Supports custom label taxonomies.

**3D Lifting**: BoxerNet operates per-detection. Given a 2D crop:
- Encode image with DINOv3
- Cross-attend with camera intrinsics (focal length, principal point) and optional semi-dense depth
- Predict 3D OBB parameters: center (x, y, z), dimensions (w, h, d), orientation quaternion

**Fusion & Tracking**:
- **Offline**: Hungarian matching across frames to merge duplicate detections
- **Online**: Frame-by-frame tracking for real-time applications
- Both modes output globally consistent per-scene 3D bounding boxes

## Results

Evaluated on multiple benchmarks and datasets:
- **CA-1M**: Indoor dataset with RGB-D sequences; Boxer achieves competitive 3D AP scores
- **SUN-RGBD**: Single-image indoor scenes; demonstrates zero-shot generalization
- **ScanNet**: Dense indoor reconstructions; strong performance on room-scale detection
- **Project Aria**: Demonstrates practical deployment on egocentric video with fisheye optics

Interactive demo shows real-time 2D-to-3D lifting on arbitrary video sequences.

## Relation to prior work

Boxer complements [[2025-spatiallm-structured-indoor-modeling|SpatialLM]] by solving the **object detection** leg of 3D scene understanding, while SpatialLM addresses holistic **scene layout and description**. Unlike SpatialLM's LLM-based structured generation, Boxer pursues task-specific neural architecture for precise bounding box geometry. Together, they represent two complementary paradigms: learned geometric lifting vs. language-based scene parsing.

Builds on OWLv2 (Minderer et al. 2023) for open-vocabulary detection and DINOv2/DINOv3 for robust feature encoding, but novel application to camera-aware 3D geometry prediction with cross-attention fusion.

## Open questions / limitations

- **Category-agnostic geometry**: BoxerNet doesn't condition on object identity during lifting — unclear if category-specific geometry priors (e.g., chairs vs. tables) could improve accuracy
- **Depth availability**: Performance likely degrades when depth is unavailable; robustness on monocular sequences with only SLAM-derived geometry not extensively evaluated
- **Outdoor scenes**: System is tuned for indoor environments; outdoor object detection and orientation remains unexplored
- **Occlusion handling**: Multi-view fusion helps but per-frame occlusion reasoning not explicitly addressed
- **Scale of scenes**: Tested on room-scale; whole-building or outdoor large-scale scenes not demonstrated
