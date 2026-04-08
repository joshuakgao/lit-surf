---
topic: video-understanding
tags: [concept, method]
---

## Definition

Data composition for video refers to strategies for reorganizing and combining existing video-text pairs during training to expand temporal diversity or improve model generalization without collecting new annotations. Rather than treating each video as an isolated sample, composition methods splice, concat, or synthetically arrange multiple videos and captions into single training instances.

## Origins

Introduced formally by [[2026-videoweave|VideoWeave]] (Durante et al., 2026), which splices short captioned videos into synthetic long-context samples for efficient long-form video understanding. Related to concatenation strategies in language model pretraining (e.g., packing, document concatenation) but adapted to multimodal sequences where both video frames and captions must align.

## Key variants / extensions

- **Random splicing**: concatenate L videos in random order; simple baseline with minimal supervision
- **Visually clustered splicing**: select videos with similar scene/action content; preserves semantic coherence but requires feature-based clustering
- **Semantically clustered splicing**: select videos with related caption themes; encourages reasoning across thematically linked content
- **Caption enrichment**:
  - Simple concatenation: "Caption1. Caption2. ..."
  - Blending: "In the first clip ... In the second clip ..." (explicit structuring)
  - Reordering/formatting: narrative or question-answer formats
- **Hierarchical composition**: future direction; multi-level temporal composition (scenes → sequences → full videos) for very long content

## Papers using this concept

- [[2026-videoweave]] — defines and evaluates the core composition framework; shows random vs. clustered trade-offs and caption enrichment strategies on video QA tasks
