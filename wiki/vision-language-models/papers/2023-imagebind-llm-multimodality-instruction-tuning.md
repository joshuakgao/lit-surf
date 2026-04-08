---
title: "ImageBind-LLM: Multi-modality Instruction Tuning"
authors: Han, Zhe; Zhang, Ziyi; Zhang, Shuhao; et al.
year: 2023
venue: NeurIPS
topic: vision-language-models
source: "[[raw/vision-language-models/2023/2023-imagebind-llm-multimodality-instruction.pdf]]"
tags: [multimodal-instruction-tuning, embedding-space-alignment, cross-modal-cache, zero-shot]
---

## Summary

ImageBind-LLM enables multimodal instruction tuning of LLMs through ImageBind's unified embedding space, allowing the model to respond to audio, 3D point clouds, video, and other modalities while only training on image-text alignment. The key innovation is a learnable bind network that aligns LLaMA's embedding space with ImageBind's image encoder, with visual instructions progressively injected into all layers via an attention-free, zero-initialized gating mechanism. During inference, a training-free visual cache model retrieves relevant image features from 3 million pre-computed ImageBind features, effectively mitigating the modality discrepancy between training (image-text) and inference (diverse modalities).

## Key contributions

- First work to enable multimodal instruction following beyond image-text through embedding space alignment with ImageBind
- Proposes progressive visual instruction injection via gating mechanism without requiring attention modifications
- Introduces training-free visual cache for handling modality gaps between training and inference
- Demonstrates zero-shot multimodal understanding across audio, video, 3D, and thermal modalities with only image-text training

## Method

Three components: (1) learnable bind network aligning LLaMA to ImageBind's space, (2) progressive visual feature injection into all transformer layers via zero-initialized gating, (3) inference-time visual cache retrieving relevant pre-computed ImageBind features for handling unseen modalities.

## Results

Demonstrates significant language generation quality across diverse modalities, with strong zero-shot performance on multimodal tasks despite training only on image-text data.

## Relation to prior work

Leverages ImageBind's emergent cross-modal alignment to extend LLaVA-style instruction tuning beyond images. Shows how alignment to a unified embedding space enables multimodal capabilities without explicit multimodal training data.

## Open questions / limitations

Depends on quality of pre-computed ImageBind feature cache. Zero-shot performance on very novel modalities or modality combinations not exhaustively evaluated. Training-inference modality gap only partially addressed.

---
