---
title: "Skip \\n: A Simple Method to Reduce Hallucination in Large Vision-Language Models"
authors: Han, Zongbo; et al.
year: 2024
venue: arXiv
topic: vision-language-models
source: "[[raw/vision-language-models/2025/2025-skip-newline-reduce-hallucination.pdf]]"
tags: [hallucination-mitigation, prompt-engineering, semantic-bias, vision-language-understanding]
---

## Summary

This paper identifies and leverages an inherent semantic shift bias in LVLMs related to paragraph breaks (\n\n) to reduce hallucinations. The key insight is that in training data, content before and after '\n\n' frequently exhibits significant semantic changes, creating a learned bias where models expect semantic shifts at paragraph boundaries. The "Skip \n" technique exploits this bias pattern, modifying how paragraph breaks are used in prompts to encourage models to generate less hallucinatory descriptions by working with rather than against these learned patterns. The approach is remarkably simple yet effective, requiring only prompt engineering modifications without model fine-tuning or architectural changes, making it broadly applicable to existing vision-language models.

## Key contributions

- Identifies semantic shift bias in LVLMs related to paragraph break patterns
- Proposes simple prompt engineering technique leveraging learned biases to reduce hallucinations
- Demonstrates effectiveness without requiring model modifications or fine-tuning
- Provides interpretable explanation for hallucination reduction mechanism

## Method

Prompt engineering approach that strategically places or omits paragraph breaks (\n\n) based on understanding of learned semantic shift biases in LVLMs, encouraging generation of more accurate descriptions.

## Results

Significant reduction in hallucinations across vision-language tasks through simple prompt modifications, with no additional computational cost.

## Relation to prior work

Addresses critical challenge of hallucinations in vision-language models through bias-aware prompt engineering, complementing other hallucination mitigation approaches and showing value of understanding model biases.

## Open questions / limitations

Semantic shift bias may vary across models and training data. Approach may not generalize equally to all LVLM architectures. Scope of bias analysis limited to paragraph breaks; other prompt patterns may have similar effects not explored.

---
