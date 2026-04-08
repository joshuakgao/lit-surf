---
title: "SpatialLM: Training Large Language Models for Structured Indoor Modeling"
authors: [Details in paper]
year: 2025
venue: NeurIPS
topic: vision-language-models
source: "[[raw/vision-language-models/2025/2025-spatiallm-structured-indoor-modeling.pdf]]"
tags: [3d-scene-understanding, indoor-layout, point-clouds, structured-output, spatial-reasoning]
---

## Summary

SpatialLM is a large language model designed to process 3D point cloud data and generate structured 3D scene understanding outputs including architectural elements (walls, doors, windows) and oriented object boxes with semantic categories. Unlike previous task-specific network designs, SpatialLM adheres to standard multimodal LLM architecture and is fine-tuned from open-source LLMs, employing a standard "Encoder-MLP-LLM" architecture for multimodal feature alignment. The system generates structured scene descriptions in pure text form as output, making 3D scene understanding more accessible through language-based representations. Researchers collected a large-scale synthetic dataset of 12,328 indoor scenes (54,778 rooms) with ground-truth 3D annotations for training, achieving state-of-the-art on layout estimation and competitive results on 3D object detection while demonstrating a feasible path for enhancing spatial understanding in modern LLMs.

## Key contributions

- Applies standard multimodal LLM architecture to 3D point cloud understanding for indoor scene modeling
- Demonstrates that fine-tuning from open-source LLMs is effective for structured 3D scene understanding
- Creates large-scale synthetic dataset with 12,328 scenes and 54,778 rooms with ground-truth 3D annotations
- Achieves state-of-the-art performance on layout estimation with text-based structured output

## Method

Standard multimodal LLM with point cloud encoder and MLP alignment layer, fine-tuned from open-source LLMs to generate text-based structured descriptions of 3D scenes including architectural elements and object locations.

## Results

State-of-the-art performance on indoor layout estimation and competitive results on 3D object detection, with effective transfer of LLM reasoning to spatial understanding tasks.

## Relation to prior work

Extends vision-language models to 3D spatial understanding, showing that standard LLM architectures can handle structured 3D scene understanding without task-specific designs. Demonstrates generalization of multimodal LLM approaches.

## Open questions / limitations

Approach relies on synthetic training data; domain gap to real scenes may limit performance. Text-based output representation may lose some spatial precision compared to explicit 3D representations. Scalability to larger scenes or more complex indoor environments not thoroughly explored.

---
