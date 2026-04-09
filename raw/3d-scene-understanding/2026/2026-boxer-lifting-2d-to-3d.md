---
title: "Boxer"
source: "https://facebookresearch.github.io/boxer/"
author:
published:
created: 2026-04-09
description:
tags:
  - "clippings"
---
Robust Lifting of Open-World 2D Bounding Boxes to 3D

Daniel DeTone, Tianwei Shen, Fan Zhang, Lingni Ma, Julian Straub, Richard Newcombe, and Jakob Engel

Meta Reality Labs Research

## What is Boxer?

Boxer lifts 2D object detections into static, global, fused 3D oriented bounding boxes (OBBs) from posed images and semi-dense point clouds. It is focused on indoor object detection and comes with a pre-trained model for running inference on a variety of data sources.

![Boxer System Architecture](https://facebookresearch.github.io/boxer/images/boxer_system.jpg)

## How It Works

Boxer uses a three-stage pipeline. First, an open-vocabulary 2D detector (OWLv2) finds objects in each frame. Then, BoxerNet lifts each 2D detection into a 3D oriented bounding box using camera intrinsics, gravity direction, and optional semi-dense depth. Finally, detections across frames can be fused offline or tracked online for temporal consistency.

### 2D Detection

OWLv2 open-vocabulary detector finds objects using text prompts or manual 2D bounding box prompts. Supports custom label taxonomies.

### 3D Lifting

BoxerNet encodes the image crop with DINOv3, cross-attends with camera and depth features, and predicts a full 3D oriented bounding box per detection.

### Fusion & Tracking

Per-frame 3D boxes are merged via offline Hungarian-algorithm fusion or online tracking for globally consistent scene-level 3D detections.

## Interactive Demo

2D bounding box prompts can be used to quickly annotate and estimate 3D oriented bounding boxes in any scene. Draw a box, and Boxer lifts it to 3D in real time. This is an example from CA-1M.

<video controls=""><source src="https://facebookresearch.github.io/boxer/images/ca1m_demo.mp4" type="video/mp4"></video>

## Supported Data Sources

Boxer works out of the box with multiple data sources. For each, it requires images, camera intrinsics, gravity direction, and optionally depth. For video sequences, 6-DoF poses enable multi-frame fusion.

### Project Aria Gen 1 & 2

Full support including fisheye cameras, VRS recordings, and semi-dense point clouds from visual-inertial SLAM.

### CA-1M

Large-scale indoor dataset with posed RGB-D sequences for benchmarking 3D object detection.

### SUN-RGBD

Single-image indoor scenes with depth maps via the Omni3D dataset interface.

### ScanNet

Dense indoor reconstructions with posed RGB-D frames for room-scale 3D detection.

## Quick Start

Get Boxer running in minutes.

### Installation

```
git clone https://github.com/facebookresearch/boxer
cd boxer
curl -LsSf https://astral.sh/uv/install.sh | sh  # install uv
uv venv boxer --python 3.12
source boxer/bin/activate
uv pip install 'torch>=2.0' numpy opencv-python tqdm dill
uv pip install projectaria-tools          # Aria support
uv pip install moderngl moderngl-window imgui-bundle  # 3D viewer
```

## Citation

If you find Boxer useful in your research, please consider citing:

```
@article{boxer2026,
      title={Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D},
      author={Daniel DeTone and Tianwei Shen and Fan Zhang and Lingni Ma and Julian Straub and Richard Newcombe and Jakob Engel},
      year={2026},
}
```