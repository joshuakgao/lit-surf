---
topic: agentic-mllms
tags: [concept, capability]
---

## Definition

Zero-shot visual reasoning is the ability to solve novel visual tasks without task-specific training data or fine-tuning. The model generalizes by recombining pretrained vision and language modules in new ways to address previously unseen queries or task formulations. Contrast with few-shot (one or more examples) and supervised learning (large annotated dataset).

## Origins

Enabled by recent advances in large pretrained models (vision transformers, multimodal LLMs) and compositional reasoning paradigms. ViperGPT demonstrates that zero-shot performance is achievable not just through scaling models, but through compositional interpretability—explicitly synthesizing task-specific reasoning programs.

## How it works

1. **Provide an API**: Expose available vision/language capabilities as function signatures
2. **Synthesize a program**: LLM generates executable code that chains available modules for the given query
3. **Execute**: Run the program on the visual input with no further training
4. **Adapt to new tasks**: A different query generates a different program; same modules, different composition

## Advantages

- **No task-specific training**: Reduces annotation burden and deployment friction
- **Interpretability**: Generated programs expose reasoning steps
- **Generalization**: Systematic transfer across novel task combinations
- **Rapid prototyping**: Easy to add new queries without collecting new labeled data

## Challenges

- **API completeness**: Heavily dependent on coverage of available modules
- **Error propagation**: Mistakes in intermediate steps affect downstream results
- **Latency**: Multiple LLM calls and sequential module invocations may be slower than end-to-end models

## Papers using this concept

- [[../papers/2023-viper-gpt|ViperGPT]] — achieves zero-shot SOTA on visual grounding, image QA, and video QA via program synthesis; shows that compositional zero-shot reasoning can outperform task-specific supervised models
