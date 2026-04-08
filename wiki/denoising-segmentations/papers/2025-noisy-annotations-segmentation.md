---
title: "Noisy Annotations in Semantic Segmentation"
authors: Kimhi, Kerem, Grad, Rivlin, Baskin
year: 2025
venue: arXiv
topic: denoising-segmentations
source: "[[raw/denoising-segmentations/2025/2025-noisy-annotations-segmentation.pdf]]"
thumbnail: "[[wiki/denoising-segmentations/papers/2025-noisy-annotations-segmentation.png]]"
tags: [segmentation, annotation-noise, robustness, benchmarks]
---

![](/wiki/denoising-segmentations/papers/2025-noisy-annotations-segmentation.png)

## Summary

Instance segmentation requires both accurate class labels and precise spatial delineation, making it uniquely vulnerable to annotation noise. This paper systematically investigates how various forms of noisy annotations—including class confusion, boundary distortions, and weak annotations from foundation models—affect segmentation model performance across multiple datasets. The authors introduce three synthetic noise benchmarks (COCO-N, CityScapes-N, VIPER-N) and one weakly-annotated benchmark (COCO-WAN) that simulate realistic annotation errors. A key clinical motivating example is echocardiography segmentation, where even 5% boundary mislabeling of cardiac chambers can shift ejection fraction (EF) calculations by 6-11 percentage points, crossing diagnostic thresholds between normal and pathological. Experimental results reveal that existing learning-from-noise (LNL) techniques struggle significantly with spatial inaccuracies in segmentation tasks.

## Key contributions

- **Systematic characterization** of annotation noise patterns in instance segmentation: class label errors, boundary misalignments, missing instances, and weak annotation tool failures
- **Three synthetic noise benchmarks** (COCO-N, CityScapes-N, VIPER-N) simulating realistic label noise on both real-world and synthetic data
- **Weakly-annotated benchmark** (COCO-WAN) leveraging promptable foundation models for natural weak supervision
- **Empirical evidence** that popular segmentation architectures experience significant performance degradation under annotation noise
- **Demonstration** that standard LNL methods fail to adequately handle spatial label inaccuracies

## Method

The paper employs a stochastic, augmentation-style approach to inject realistic label noise into segmentation datasets. Noise types include:
- **Class confusion**: incorrect semantic labels
- **Boundary distortions**: shifted, shrunk, or expanded masks
- **Missing instances**: completely absent objects from annotations
- **Weak annotation noise**: errors from foundation models (e.g., SAM) when prompted with misaligned bounding boxes or ambiguous descriptions

The COCO-WAN benchmark specifically uses promptable segmentation models (like SAM) with deliberately imperfect prompts to generate realistic weak supervision.

## Results

- Even modest annotation errors (e.g., small boundary shifts) lead to notable segmentation quality drops across mIoU, mask AP, and other metrics
- Performance degradation varies significantly across datasets and model architectures
- Current LNL techniques (designed primarily for classification) fail to adequately address spatial inaccuracies
- Medical imaging applications (e.g., cardiac volume measurement) are particularly sensitive to boundary noise

## Relation to prior work

This work extends learning-from-noise research, which has primarily focused on image classification and medical imaging in isolation. The paper bridges this gap by providing a comprehensive empirical study of noise robustness specifically for instance segmentation across diverse domains. It complements concurrent work on data quality in computer vision and motivates the need for segmentation-specific noise-robust training strategies.

## Open questions / limitations

- How to develop noise-aware training strategies specifically tailored for spatial prediction tasks?
- Can modern segmentation models be made inherently robust to annotation noise without requiring noise labels or synthetic benchmarks?
- How do different sources of noise (human error vs. automated tool errors) interact?
- Does noise robustness transfer across different datasets and domains?
