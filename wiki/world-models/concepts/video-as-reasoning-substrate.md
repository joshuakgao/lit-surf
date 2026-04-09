---
topic: video-reasoning
tags: [concept, method]
---

## Definition

Video as a reasoning substrate treats video sequences as a medium for grounding and expressing intelligent reasoning over spatiotemporal structure. Unlike video for visual realism or content description, this paradigm emphasizes video's ability to naturally encode spatial relationships, physical dynamics, temporal continuity, and causal interactions.

## Origins

Emerging field. Recent work (Wiedemer et al., 2025; Tong et al., 2025; Guo et al., 2025) explores whether generative video models (Sora, Veo) exhibit reasoning capabilities. VBVR (2026) formalizes this by proposing video reasoning as a systematic research area with large-scale training data and verifiable evaluation.

## Key variants / extensions

- **Zero-shot reasoning from generative models**: Sora, Veo exhibit non-trivial reasoning in zero-shot settings without explicit reasoning training (Wiedemer et al., 2025)
- **Supervised reasoning training**: VBVR and related work train models explicitly on reasoning tasks, showing that supervised tuning outperforms zero-shot
- **Chain-of-Frame reasoning**: Multi-step diagnostic chains where intermediate video frames clarify reasoning steps (Guo et al., 2025; Liu et al., 2025)
- **Counterfactual video reasoning**: Generating "what if?" videos to reason over hypotheticals and causal structure (emerging area)

## Papers using this concept

- [[2026-vbvr-very-big-video-reasoning|VBVR]] — frames video as a reasoning substrate; datasets and scaling studies demonstrate that supervised reasoning training enables systematic progress
