---
topic: video-reasoning
tags: [concept, method]
---

## Definition

Verifiable evaluation enforces reproducible, rule-based scoring for assessing model performance rather than relying on language model judges (VLM-as-judge paradigms). Rules are deterministic, transparent, and aligned with human judgment, enabling interpretable diagnosis of reasoning capabilities.

## Origins

Emerged as a counterpoint to VLM-as-judge evaluation, which has become standard for evaluating video generation and understanding (Peng et al., 2025). The concern: VLM judges are opaque, non-reproducible across runs/models, and may embed their own biases. Rule-based evaluation provides an alternative that is verifiable and interpretable.

## Key variants / extensions

- **Rule-based scorers**: Deterministic logic per task type (e.g., spatial containment checks, motion magnitude bounds, semantic label matching)
- **Human-aligned metrics**: Rules are validated against human judgment; correlation with human annotations ensures alignment
- **Per-task specialization**: Each task has its own scoring logic matched to its reasoning requirement (Spatiality ≠ Abstraction)
- **Explainable diagnosis**: Rule-based scores can be traced to specific reasoning failures, enabling targeted improvement

## Papers using this concept

- [[2026-vbvr-very-big-video-reasoning|VBVR]] — introduces VBVR-Bench with rule-based scorers for 200 tasks; demonstrates that verifiable evaluation enables reproducible, interpretable scaling studies
