---
title: "ClipCap: CLIP Prefix for Image Captioning"
authors: Mokady, Ron; Hertz, Amir; Bermano, Amit H.
year: 2021
venue: arXiv
topic: vision-language-models
source: "[[raw/vision-language-models/2021/2021-clip-prefix-image-captioning.pdf]]"
tags: [image-captioning, clip, prefix-tuning, parameter-efficient]
---

## Summary

ClipCap proposes a simple yet effective approach to image captioning by bridging frozen CLIP image encodings with a pre-trained GPT-2 language model using a learned prefix mapping network. The key insight is that a lightweight trainable mapping network (prefix) can effectively translate visual representations from CLIP into the embedding space of a frozen language model, enabling high-quality image captioning without fine-tuning either foundational model. The approach achieves state-of-the-art results on Conceptual Captions and nocaps benchmarks while being significantly more parameter-efficient and faster to train than existing methods, requiring only 1.2M publicly available data and achieving full training in one day on a single 8-A100 node.

## Key contributions

- Introduces the prefix-tuning approach for vision-language alignment, enabling efficient knowledge transfer between frozen models
- Demonstrates that a small learnable mapping network can bridge the gap between visual and textual embedding spaces
- Achieves comparable performance to state-of-the-art methods with substantially fewer parameters and faster training time
- Shows strong generalization on challenging zero-shot evaluation benchmarks

## Method

The approach uses CLIP-ViT image encodings as input, processes them through a lightweight MLP projection network (the "prefix"), and feeds the resulting embeddings to a frozen GPT-2 language model. The prefix network learns to translate visual tokens into a format compatible with the language model's embedding space, allowing coherent caption generation without modifying either the vision or language model.

## Results

Achieves strong performance on Conceptual Captions and nocaps datasets, with particular strength on zero-shot and out-of-distribution benchmarks where the simple parametrization generalizes well beyond the training distribution.

## Relation to prior work

Builds directly on CLIP and represents an early efficient approach to bridging vision and language without fine-tuning large models. Precedes more complex multimodal architectures like LLaVA and serves as a foundational approach to prefix-based alignment.

## Open questions / limitations

Limited to caption generation task; unclear how well the prefix approach extends to other vision-language tasks. Relies on frozen CLIP and GPT-2, potentially limiting model capability compared to end-to-end training.

---
