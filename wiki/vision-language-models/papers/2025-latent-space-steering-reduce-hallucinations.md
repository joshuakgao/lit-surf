---
title: "Reducing Hallucinations in Vision-Language Models via Latent Space Steering"
authors: Liu, Sheng; Ye, Haotian; Xing, Lei; Zou, James
year: 2024
venue: EMNLP
topic: vision-language-models
source: "[[raw/vision-language-models/2025/2024-vti-latent-space-steering.pdf]]"
tags: [hallucination-mitigation, latent-space-intervention, test-time-inference, vision-encoder-stability]
---

## Summary

This paper introduces Visual and Textual Intervention (VTI), a test-time technique that reduces hallucinations in LVLMs by steering latent space representations during inference to enhance vision feature stability. The key insight is that hallucinations often arise from misalignments between separately pre-trained vision encoders and text decoders, with text decoders showing excessive sensitivity to vision inputs. VTI addresses this by intervening in the latent space representations to promote better alignment between modalities. As a task-agnostic test-time intervention, VTI can be applied to any problem without additional computational cost beyond standard inference. The approach demonstrates that careful manipulation of intermediate representations can significantly reduce problematic hallucinations while maintaining generation quality.

## Key contributions

- Identifies vision-text decoder sensitivity as source of hallucinations in separately pre-trained models
- Proposes task-agnostic latent space steering for hallucination reduction at test time
- Demonstrates effectiveness without additional training or fine-tuning requirements
- Provides interpretable mechanism for understanding hallucination sources

## Method

Test-time intervention technique that manipulates latent space representations of vision and text tokens to reduce sensitivity of text decoder to vision inputs, promoting more stable and accurate generation.

## Results

Significant hallucination reduction across diverse vision-language tasks without requiring model retraining, with minimal computational overhead.

## Relation to prior work

Complements other hallucination reduction approaches like prompt engineering (Skip \n) by addressing the fundamental alignment issue between vision and text encoders, offering test-time solution without model modification.

## Open questions / limitations

Optimal steering magnitude and target directions may vary across models and tasks. Approach assumes decomposability of hallucination sources into vision-text misalignment; other causes not addressed. Generalization to different model architectures and training procedures not exhaustively evaluated.

---
