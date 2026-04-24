---
title: "GLaMM: Pixel Grounding Large Multimodal Model"
authors: Rasheed, Hanoona; Maaz, Muhammad; Khan, Salman; Zamir, Amir; Shao, Longhui; Khan, Fahad S.
year: 2024
venue: CVPR
topic: vision-language-models
source: "[[raw/vision-language-models/2024/2024-glamm-pixel-grounding-multimodal.pdf]]"
tags: [pixel-grounding, semantic-segmentation, conversational-grounding, dense-annotation]
---

## Summary

GLaMM is the first Large Multimodal Model capable of generating natural language responses seamlessly integrated with corresponding object segmentation masks, unifying textual and visual grounding in a single model. Unlike prior region-level LMMs limited to single object categories or requiring explicit region specification, GLaMM flexibly accepts textual and optional visual prompts to generate both text responses and pixel-level segmentation masks. The authors introduce a Grounded Conversation Generation (GCG) task requiring densely grounded concepts in natural scenes and create the Grounding-anything Dataset (GranD) with 7.5M unique concepts grounded in 810M regions with segmentation masks using an automated annotation pipeline. GLaMM demonstrates effectiveness beyond GCG on downstream tasks including referring expression segmentation, image captioning, region-level captioning, and vision-language conversations.

## Key contributions

- First LMM combining dense textual and pixel-level visual grounding in unified natural language output
- Introduces Grounded Conversation Generation task and comprehensive evaluation protocol for grounding quality
- Creates GranD dataset with 810M densely grounded regions, enabling large-scale training for grounded tasks
- Demonstrates flexible multimodal prompting (text and visual) for grounding tasks

## Method

Vision-language architecture enhanced with segmentation capabilities, trained on GranD dataset using automated annotation pipeline to generate both text and segmentation masks for complex visual scenes.

## Results

Strong performance on grounded conversation generation, referring expression segmentation, and region-level vision-language understanding tasks, with particular strength in dense grounding and complex scene understanding.

## Relation to prior work

Advances LMMs beyond simple pointing/bounding boxes to full pixel-level grounding. Builds on LLaVA-style architectures while adding dense prediction capabilities and introduces the comprehensive GranD dataset for grounding research.

## Open questions / limitations

Segmentation generation adds computational complexity and may slow inference. Quality of automatically generated annotations in GranD may vary across different object categories. Scalability to even larger scale grounding tasks not fully explored.

---
