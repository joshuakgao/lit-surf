---
topic: 3d-scene-understanding
---

# 3D Scene Understanding — Overview

*Last updated: 2026-04-09 | Sources: 2 papers*

## Current thesis

3D scene understanding is branching into two complementary paradigms: **LLM-based structured generation** and **learned geometric lifting from 2D**. SpatialLM (2025) establishes that LLMs can process point clouds and generate holistic scene descriptions (layout + objects) — the "what and where" via language. Boxer (2026) tackles the orthogonal problem of precise **object localization and geometry** via open-world 2D-to-3D lifting — the "oriented boxes" for fine-grained spatial reasoning. Together, these papers suggest 3D scene understanding is converging on a hybrid architecture: language models for high-level scene semantics, neural geometric models for precise object geometry and alignment.

## Key trends

**2025:**
- **LLMs enter structured 3D reconstruction.** SpatialLM (NeurIPS 2025) is the first empirical demonstration that a small LLM (0.5B) can process raw point clouds and output accurate structured scene descriptions competitive with specialised geometric methods.
- **Text-as-structure is gaining traction.** SceneScript (2024) and SpatialLM (2025) both use structured text output for 3D scenes, avoiding task-specific decoders. This format is editable, interpretable, and compatible with the growing ecosystem of LLM tooling.
- **Synthetic, high-quality datasets are critical.** The SpatialLM dataset (54,778 rooms, fully human-authored) enables LLM pre-training at scale. Without it, LLMs trained only on small real datasets (e.g., ScanNet) underperform specialised detectors.
- **Zero-shot generalisation to video.** SpatialLM demonstrates that models trained on RGBD point clouds can transfer to monocular video-reconstructed point clouds (via SLAM), opening the door to deployment without depth sensors.

**2026:**
- **Open-world 2D-to-3D lifting emerges.** Boxer (Meta Reality Labs, 2026) shifts the 3D detection paradigm from category-specific training to **open-world lifting**: OWLv2 finds objects from text prompts, then BoxerNet predicts full 3D geometry without per-category supervision. This orthogonal approach complements SpatialLM by providing precise, oriented bounding boxes rather than holistic scene descriptions.
- **Camera geometry is the bridge.** Boxer demonstrates that explicit camera intrinsics and gravity direction, combined with optional depth, are sufficient priors for lifting 2D detections to precise 3D geometry. This suggests a principled architectural pattern: geometry-aware cross-attention for 2D-to-3D reasoning.
- **Multi-view consistency via fusion.** Boxer's offline Hungarian matching and online tracking for merging per-frame detections establishes a practical fusion standard for video-based 3D understanding, avoiding the need for explicit 3D annotations.

## Open problems

- **Open-vocabulary 3D detection (partially addressed)**: Boxer tackles this for 2D-to-3D lifting, but holistic scene understanding with arbitrary object classes remains open
- **Real-world scan generalisation**: models trained on synthetic scenes degrade on real scans with noise, clutter, and incomplete coverage; Boxer works on real data but robustness on heavily occluded/cluttered scenes unclear
- **Outdoor and large-scale scenes**: all work is exclusively indoor; urban-scale 3D understanding and open-world detection remains unexplored
- **LLM scale**: only small LLMs (0.5B) have been tested; whether larger models bring qualitative improvements to spatial reasoning is unknown
- **Multi-room and multi-floor scenes**: both SpatialLM and Boxer handle rooms individually; whole-building understanding is out of scope
- **Category-agnostic geometry**: Boxer doesn't condition on object identity during 3D lifting; whether category-specific geometry priors (e.g., chairs vs. tables) could improve accuracy is unexplored
- **Hybrid LLM + geometric reasoning**: how to optimally combine SpatialLM's scene descriptions with Boxer's precise bounding boxes for downstream tasks remains an open design question

## Contradictions and debates

- **Synthetic vs. real data**: SpatialLM shows strong results using synthetic data for pre-training, but real-world evaluation on ScanNet still requires fine-tuning — the domain gap is not fully bridged

## Recommended reading order

1. [[papers/2025-spatiallm-structured-indoor-modeling|SpatialLM (2025)]] — establishes the LLM-for-3D paradigm, architecture, dataset, and benchmark comparisons; essential entry point for holistic scene understanding
2. [[papers/2026-boxer-lifting-2d-to-3d|Boxer (2026)]] — orthogonal approach for precise object geometry via 2D-to-3D lifting; read after SpatialLM to understand the complementary paradigm
   - If interested in open-world detection specifically, start here; if interested in structured scene generation, start with SpatialLM
