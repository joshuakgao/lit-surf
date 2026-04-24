---
topic: world-models
tags: [concept, method]
---

## Definition

A technique for extracting task-specific visual structures from a trained world model without additional supervision. By comparing model predictions under ground-truth inputs versus counterfactual (modified) inputs, the difference in predictions serves as a zero-shot readout for that visual factor. Approximates causal inference by isolating the causal effect of a visual variable on model behavior.

## Origins

Operationalized in [[../papers/2026-babyzwm-zero-shot-world-models|BabyZWM]] as a general interface for zero-shot task extraction from self-supervised predictors. Related to classical causal inference methods (e.g., do-calculus, instrumental variables) but adapted to the visual domain via neural network interventions.

## Key variants / extensions

- **Ground-truth vs. counterfactual comparison** (BabyZWM): Given a trained predictor, mask a visual variable of interest (e.g., depth information) and compare predictions with/without that variable. The prediction difference approximates the causal contribution of that variable.
- **Gradient-based attribution**: Alternative approach using neural network gradients to identify which inputs most affect predictions.
- **Causal graphs and structural equation models**: More formal causal approaches that require explicit graph structure but may not scale to high-dimensional visual data.

## Papers using this concept

- [[../papers/2026-babyzwm-zero-shot-world-models|BabyZWM]] — extracts depth, optical flow, segmentation, and intuitive physics predictions zero-shot via approximate causal inference on the trained predictor

