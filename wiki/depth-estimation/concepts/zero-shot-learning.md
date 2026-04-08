---
topic: depth-estimation
tags: [concept, method]
---

## Definition

Zero-shot learning in computer vision refers to performing a task on test data without task-specific training examples. The model relies on general prior knowledge (from pre-training on large-scale data) rather than supervised fine-tuning on the target task. This is particularly powerful for dense prediction tasks where obtaining dense ground truth annotations is expensive.

## Origins

Zero-shot paradigms became prominent with vision-language models (CLIP, 2021) and have been extended to dense prediction through pre-trained generative models like Stable Diffusion and diffusion transformers.

## Key variants / extensions

- **Cross-dataset zero-shot**: Generalization to unseen test datasets (e.g., MiDaS)
- **Foundation model zero-shot**: Using pre-trained models without any task-specific training (depth from Stable Diffusion)
- **Few-shot variants**: Using minimal examples (1-shot, few-shot) to adapt pre-trained models

## Papers using this concept

- [[2026-fe2e-from-editor-to-dense-geometry-estimator]] — Achieves zero-shot depth/normal estimation without task-specific training, demonstrating that editing models provide strong geometry priors
