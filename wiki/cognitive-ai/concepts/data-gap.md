---
topic: cognitive-ai
tags: [concept, challenge]
---

## Definition

The efficiency gap between human and machine learners: humans (especially infants and children) achieve sophisticated cognitive abilities with orders of magnitude less training data than current AI systems require. For example, human children learn language from ~10–100 million words; large language models require ~100 billion words. Similarly, children learn object categories and visual concepts from handfuls of examples; supervised deep learning requires millions of labeled images.

## Origins

Documented in developmental psychology and cognitive science research (Frank et al., Brown et al.). Formalized as a research challenge in [[../papers/2025-babyview-egocentric-video-dataset|BabyView]], which quantifies performance gaps between models trained on naturalistic child-scale data vs. curated large-scale datasets.

## Key variants / extensions

- **Sample efficiency gap**: Humans learn from dramatically fewer examples (few-shot learning)
- **Data quality vs. quantity**: Humans learn from noisy, unbalanced, naturalistic data; AI systems often require clean, curated, large-scale data
- **Generalization from limited data**: Humans transfer learned knowledge flexibly to new domains; AI systems often require extensive retraining or fine-tuning
- **Architecture-data co-dependence**: Some "data efficiency" is really architectural efficiency; question remains whether the gap is primarily data or inductive bias

## Papers using this concept

- [[../papers/2025-babyview-egocentric-video-dataset|BabyView]] — quantifies data gap by measuring model performance on naturalistic child video vs. curated benchmarks
- [[../../world-models/papers/2026-babyzwm-zero-shot-world-models|BabyZWM]] — proposes architectural innovations to close the data gap; demonstrates learning world models from human-scale data

