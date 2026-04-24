---
topic: world-models
tags: [concept, method]
---

## Definition

A framework for evaluating how a model's capabilities develop over the course of training, using developmental psychology as an inspiration and reference. Rather than evaluating only final performance, researchers assess intermediate checkpoints to see if learning milestones emerge in an order consistent with human infant development. This provides both a validation signal (developmental plausibility) and a lens for understanding how complex visual-cognitive abilities build from simpler foundations.

## Origins

Grounded in developmental psychology research on infant visual cognition and object understanding. [[../papers/2026-babyzwm-zero-shot-world-models|BabyZWM]] applies this framework computationally, showing that a model trained on naturalistic child video exhibits learning progressions that parallel documented developmental milestones (e.g., motion perception before object permanence understanding).

## Key variants / extensions

- **Behavioral trajectory**: Compare model performance across tasks at different training checkpoints to documented ages of skill emergence in infants (e.g., "depth perception emerges at X months, object permanence at Y months").
- **Neural trajectory**: Compare learned representations at different training stages to neural recording data (fMRI, electrophysiology) from infants at corresponding developmental stages.
- **Curriculum learning**: Explicitly design training curricula (order of tasks, data presentation) to mimic natural developmental sequences, hypothesizing that this inductive bias will improve learning efficiency.

## Papers using this concept

- [[../papers/2026-babyzwm-zero-shot-world-models|BabyZWM]] — evaluates task performance across training checkpoints and shows alignment with infant developmental trajectories; internal representations correlate with fMRI responses

