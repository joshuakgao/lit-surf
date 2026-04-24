---
title: "BodyShapeGPT: SMPL Body Shape Manipulation with LLMs"
authors: Árbol, Baldomero R.; Casas, Dan
year: 2024
venue: ECCV Workshop
topic: vision-language-models
source: "[[raw/vision-language-models/2024/2024-bodyshapegpt-3d-body-shape-manipulation.pdf]]"
tags: [3d-human-bodies, natural-language-control, avatar-generation, shape-parameters]
---

## Summary

BodyShapeGPT explores using fine-tuned LLMs to understand physical descriptions of people and create accurate 3D avatar representations using SMPL-X by inferring shape parameters from natural language. This work demonstrates that LLMs can be trained to understand and manipulate the shape space of SMPL, enabling control of 3D human shapes through natural language descriptions. The authors created a dataset of 21,000 natural language descriptions of avatars paired with gender-neutral SMPL-X shape parameters, enabling the first systematic study of language-to-3D-shape mapping. The approach promises improved human-machine interaction and opens avenues for customization and simulation in virtual environments, bridging language understanding with 3D human body modeling.

## Key contributions

- Demonstrates LLMs can learn to map natural language descriptions to 3D SMPL-X shape parameters
- Creates large-scale dataset pairing 21,000 natural language descriptions with SMPL-X parameters
- Enables natural language-based 3D avatar generation and customization
- Opens new possibilities for language-guided 3D human modeling and virtual embodiment

## Method

Fine-tuned LLM trained on dataset of natural language descriptions paired with SMPL-X shape parameters, learning to generate shape parameters from textual descriptions of human physical characteristics.

## Results

Successful mapping of natural language descriptions to realistic 3D avatar shapes, enabling intuitive avatar generation through language instructions.

## Relation to prior work

Novel application of instruction-tuning paradigm from vision-language models to 3D human body modeling, bridging natural language understanding with parametric 3D representations.

## Open questions / limitations

Dataset limited to 21,000 descriptions; scaling to more diverse descriptions needed. SMPL-X parameter space may not capture all aspects of human body variation. Gender-neutral approach may not fully address gender-specific body characteristics. Generalization to non-standard body shapes or morphologies not extensively evaluated.

---
