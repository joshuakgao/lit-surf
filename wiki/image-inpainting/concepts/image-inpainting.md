---
topic: image-inpainting
tags: [concept, task]
---

## Definition

Image inpainting (or image completion/restoration) is the task of filling missing or corrupted regions in an image in a way that appears natural and semantically coherent. The approach must handle "ill-posed" problems—multiple plausible solutions exist, requiring strong prior knowledge about image content and structure. Inpainting can be unconditional (generative), or guided by additional information (text, reference images, spatial masks, color strokes).

## Origins

Early inpainting used low-level texture synthesis or patch-based methods. GAN-based approaches emerged with ContextEncoder (2016), establishing encoder-decoder architecture as standard. Recent diffusion-based methods (RePaint, 2022+) leverage pre-trained generative models for improved semantic understanding and flexibility.

## Key variants / extensions

- **Free-form inpainting**: Arbitrary mask shapes (vs. structured masks)
- **Unconditional**: No additional guidance beyond the masked image
- **Text-guided**: Text descriptions control inpainted content
- **Reference-based**: Reference image guides restoration
- **Exemplar-driven**: Example image provides appearance/identity guidance
- **Interactive**: Stroke-based or mask-precision controls for user input

## Papers using this concept

- [[2022-repaint-inpainting-diffusion]] — Foundational diffusion-based approach generalizing to arbitrary masks
- [[2022-smartbrush-text-shape-guided-inpainting]] — Combines text and shape guidance with precision control
- [[2023-unipaint-multimodal-inpainting]] — Unified framework supporting multiple guidance modalities
- [[2025-corrfill-reference-based-inpainting]] — Reference-based inpainting with correspondence guidance
