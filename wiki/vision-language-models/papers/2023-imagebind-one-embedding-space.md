---
title: "ImageBind: One Embedding Space To Bind Them All"
authors: Girdhar, Rohit; El-Nouby, Alaaeldin; Singh, Mannat; et al.
year: 2023
venue: CVPR
topic: vision-language-models
source: "[[raw/vision-language-models/2023/2023-imagebind-one-embedding-space.pdf]]"
tags: [unified-embeddings, cross-modal-alignment, zero-shot-transfer, emergent-capabilities]
---

## Summary

ImageBind learns a joint embedding space across six modalities—images, text, audio, depth, thermal, and IMU data—using only image-paired data as the binding modality. The key insight is that all modalities need not be paired with each other; by aligning each modality's embedding to image embeddings, an emergent cross-modal alignment is automatically achieved across all combinations. This elegant approach enables novel applications including cross-modal retrieval, composing modalities with arithmetic operations, and cross-modal detection and generation, all with zero-shot generalization to new tasks. The approach leverages recent large-scale vision-language models (like CLIP), extending their capabilities to new modalities through natural image pairings.

## Key contributions

- Demonstrates that image-pairing alone is sufficient to bind multiple modalities into a shared embedding space
- Introduces emergent cross-modal alignment without explicit paired training between all modality combinations
- Enables zero-shot transfer to new modalities by leveraging image relationships
- Shows strong performance on emergent tasks (arithmetic composition, cross-modal retrieval, detection)

## Method

Each modality encoder is trained to align its embeddings with image encodings using contrastive learning objectives. The resulting aligned embeddings across modalities automatically achieve emergent alignment without direct supervision between non-image modality pairs.

## Results

Achieves state-of-the-art on emergent zero-shot recognition tasks across modalities, outperforming specialist supervised models trained specifically for individual modality pairs.

## Relation to prior work

Advances beyond CLIP's image-text alignment to truly multimodal unification. Foundational for subsequent work like ImageBind-LLM and NExT-GPT that leverage this unified embedding space.

## Open questions / limitations

Quality of embeddings may vary across modalities due to varying amounts and quality of available paired data. Not all modalities benefit equally from image-pairing approach. Scalability to additional modalities beyond the six studied not extensively explored.

---
