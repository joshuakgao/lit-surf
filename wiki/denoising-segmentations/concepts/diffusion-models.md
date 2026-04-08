---
topic: denoising-segmentations
tags: [concept, method, architecture]
---

## Definition

Diffusion models are generative models that learn to reverse a diffusion process—a gradual corruption of data through iterative noise addition. During generation, the model iteratively denoises noise back into samples from a learned distribution. Diffusion can be continuous (Gaussian noise in standard formulation) or discrete (bit-level or categorical noise for discrete data).

## Origins

Denoising diffusion probabilistic models (DDPMs) were introduced as an alternative to GANs and VAEs for image generation, offering superior stability and quality. They've since become foundational for text-to-image generation (DALL-E, Stable Diffusion) and are increasingly applied to perception and dense prediction tasks.

## Key variants / extensions

- **Continuous diffusion**: Gaussian noise schedules, most common for images and continuous data
- **Discrete diffusion**: Categorical or bit-level noise, better suited for discrete data like segmentation masks
- **Conditional diffusion**: Guided generation from input image or text conditions
- **Score-based models**: Equivalent formulation using score matching instead of noise prediction
- **Latent diffusion**: Operating in learned latent spaces for efficiency

## Papers using this concept

- [[2023-denoising-diffusion-semantic-segmentation]] — Applies discrete diffusion to model segmentation mask priors, improving semantic segmentation quality
- [[2025-noisy-annotations-segmentation]] — Studies robustness to annotation noise, distinct from but related to diffusion-based approaches
