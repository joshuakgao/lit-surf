---
title: "LlamaV-o1: Rethinking Step-by-step Visual Reasoning in LLMs"
authors: Thawakar, Omkar; et al.
year: 2025
venue: ACL
topic: vision-language-models
source: "[[raw/vision-language-models/2025/2025-llamav-o1-step-by-step-reasoning.pdf]]"
tags: [visual-reasoning, multi-step-reasoning, curriculum-learning, reasoning-benchmark]
---

## Summary

LlamaV-o1 addresses the critical need for step-by-step visual reasoning in large multimodal models, as complex multi-step visual understanding requires sequential, coherent reasoning. The paper introduces three key contributions: a visual reasoning benchmark with 4,000+ reasoning steps across eight diverse categories from visual perception to scientific reasoning; a novel step-level reasoning metric assessing correctness and logical coherence at each step rather than just task accuracy; and LlamaV-o1, a multimodal reasoning model trained with multi-step curriculum learning where tasks are progressively organized for structured learning. LlamaV-o1 outperforms existing open-source models and shows favorable performance against proprietary models, achieving 67.3% average score with 3.8% gain over LLaVA-CoT while being 5x faster during inference scaling, demonstrating that systematic reasoning training improves both accuracy and efficiency.

## Key contributions

- Introduces comprehensive visual reasoning benchmark with 4,000+ reasoning steps across diverse domains
- Proposes step-level reasoning evaluation metric assessing quality at granular step level
- Demonstrates effectiveness of multi-step curriculum learning for visual reasoning in multimodal models
- Achieves superior performance with improved inference efficiency compared to existing approaches

## Method

Multimodal model with multi-step curriculum learning approach where tasks are progressively organized by difficulty and domain, enabling systematic learning of step-by-step reasoning for visual understanding.

## Results

Superior performance to open-source models and favorable comparison to proprietary models on visual reasoning tasks, with particular strength in complex multi-step problems requiring scientific and mathematical reasoning about visual content.

## Relation to prior work

Extends vision-language models beyond single-step understanding to explicit multi-step reasoning, building on curriculum learning principles and showing that structured training significantly improves reasoning capability.

## Open questions / limitations

Curriculum design and task ordering may significantly impact performance; optimal curricula not fully explored. Benchmark limited to eight categories; broader domain coverage needed. Generalization to reasoning about images outside benchmark domains not extensively evaluated.

---
