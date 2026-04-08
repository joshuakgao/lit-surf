---
topic: vision-language-models
tags: [concept, method, evaluation]
---

## Definition

Cross-modal tokenization is the process of encoding both vision and text modalities into a unified token sequence for processing by a multimodal model. A critical aspect is how to count/measure "length" when mixing tokens of different types (vision vs. text). Standardized cross-modal tokenization counts both vision patches (from visual encoder) and text tokens together, enabling fair comparison of long-context capability across different image types and text amounts.

## Origins

Emerged as a challenge in evaluating long-context VLMs: different benchmarks counted length inconsistently (some counted images, others counted tokens from a specific vision encoder, some ignored vision tokens). MMLongBench introduced a consensus approach: counting vision patches from current-practice vision encoders (with 2×2 pixel unshuffle) alongside text tokens, enabling standardized evaluation.

## Key variants / extensions

- **Vision patch counting**: number of patches produced by vision encoder (e.g., InternVL3, Qwen2.5-VL); consistent with current practice
- **Unshuffle operations**: 2×2 pixel unshuffle reduces patch count and affects total token budget
- **Vision encoder variants**: different encoders produce different token counts for the same image; standardization requires clear encoder choice
- **Interleaving strategies**: how vision patches are interleaved with text in the sequence
- **Length normalization**: whether context length is reported as total tokens, text-only tokens, or image count

## Papers using this concept

- [[2025-mmlongbench|MMLongBench (2025)]] — introduces standardized cross-modal tokenization counting vision patches (via unshuffle) + text tokens; enables evaluation at five fixed context lengths (8K–128K); makes fair comparison of long-context VLMs possible across diverse image types and models
