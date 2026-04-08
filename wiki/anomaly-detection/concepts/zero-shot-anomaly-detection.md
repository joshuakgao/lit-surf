---
topic: anomaly-detection
tags: [concept, foundation-models, generalization]
---

## Definition

Zero-shot anomaly detection refers to detecting anomalies without task-specific training on the target domain. Rather than fine-tuning models on normal/anomalous samples from the target task, zero-shot approaches leverage pre-trained foundation models and transfer their knowledge directly to new anomaly detection problems without retraining.

## Origins

Emerged from the success of foundation models (CLIP, SAM, GPT-4) that demonstrate strong zero-shot capabilities in vision and language tasks. Transferred to anomaly detection to address the chronic problem of data scarcity — real anomalies are rare and costly to collect, making task-specific training impractical.

## Key variants / extensions

- **Foundation model adaptation (GeSCF)**: adapt segmentation models (SAM) for change detection without training; use geometric and semantic reasoning
- **Multi-model composition (DynamicEarth)**: combine multiple foundation models (SAM, CLIP, Grounding DINO) to orchestrate complex reasoning
- **Test-time generation (AnomalyAny)**: generate anomalies at test time using pre-trained diffusion models; condition on single normal sample
- **Prompt-based approaches**: guide pre-trained models via text prompts rather than labeled training data

## Papers using this concept

- [[papers/2024-towards-generalizable-scene-change-detection|GeSCF (2024)]] — zero-shot scene change detection via SAM adaptation; achieves domain generalization without training
- [[papers/2025-dynamicearth-open-vocabulary-change-detection|DynamicEarth (2025)]] — composes foundation models for open-vocabulary change detection without task-specific training
- [[papers/2025-unseen-visual-anomaly-generation|AnomalyAny (2025)]] — test-time anomaly generation using frozen Stable Diffusion
