# Depth Estimation — Overview

*Last updated: 2026-04-07 | Sources: 1 paper*

## Current thesis

Pre-trained image editing models (diffusion transformers) provide superior geometric priors for monocular depth and normal estimation compared to text-to-image generators. Editing models' inherent structural understanding enables effective zero-shot transfer with minimal training data, achieving state-of-the-art results while being dramatically more parameter-efficient than supervised baselines trained on massive datasets.

## Key trends

The field is transitioning from supervised learning (MiDaS, DPT, KITTI-specific models) to foundation model leveraging:
1. **Generative priors**: Using pre-trained models for geometry prediction (Stable Diffusion → DepthAnything → editing models)
2. **Zero-shot paradigms**: Eliminating task-specific training through effective prior transfer
3. **Efficiency**: Achieving SoTA with 100× less training data through better architectural foundations
4. **Architectural choices matter**: Image-to-image editing models prove fundamentally better than text-to-image for dense geometric tasks

## Open problems

- How to further improve geometric accuracy without access to large-scale depth annotations?
- Can editing model priors transfer to other dense geometric tasks (optical flow, surface reconstruction, surface normal from multiple views)?
- What are the theoretical properties that make editing models better for dense prediction?
- How do different diffusion model architectures and training strategies impact downstream geometric prediction?
- Can these approaches scale to high-resolution or real-time applications?

## Contradictions and debates

*No contradictions yet—early in topic development.*

## Recommended reading order

1. Start with [[papers/2026-fe2e-from-editor-to-dense-geometry-estimator|FE2E]] for a thorough overview of editing model foundations and their advantages for geometric prediction
2. Explore concept pages ([[concepts/monocular-depth-estimation|Monocular Depth Estimation]], [[concepts/dense-prediction|Dense Prediction]], [[concepts/zero-shot-learning|Zero-Shot Learning]]) to understand the broader context
