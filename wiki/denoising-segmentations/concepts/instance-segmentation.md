---
topic: denoising-segmentations
tags: [concept, task]
---

## Definition

Instance segmentation is the task of identifying and delineating individual object instances in an image, assigning each pixel both a semantic class label and an instance ID. Unlike semantic segmentation (which only requires class labels per pixel), instance segmentation requires precise spatial boundaries for each distinct object—a requirement that makes it particularly vulnerable to annotation noise.

## Origins

Instance segmentation emerged as a key computer vision task with datasets like COCO (2014) and frameworks like Mask R-CNN (2017). The task is fundamental to real-world applications including autonomous driving, medical imaging, and robotics.

## Key variants / extensions

- **Panoptic segmentation**: Combines instance and semantic segmentation, assigning both instance IDs and classes to all pixels
- **Open-vocabulary instance segmentation**: Using foundation models (SAM, CLIP) to segment novel object categories
- **Noisy instance segmentation**: Robustness to imperfect annotations, a growing concern for real-world deployment

## Papers using this concept

- [[2025-noisy-annotations-segmentation]] — Shows that instance segmentation models are uniquely sensitive to boundary noise and class confusion due to spatial precision requirements
