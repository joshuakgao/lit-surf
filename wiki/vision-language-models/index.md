---
topic: vision-language-models
---

# Vision-Language Models — Index

Research on models that jointly understand and generate language grounded in visual inputs (images and video), spanning foundation models, instruction tuning, multimodal generation, specialized vision tasks, and domain-specific applications. Focus on architectural innovations, training paradigms, and capability expansion across modalities.

## Papers by year

### 2025
- [[papers/2025-describe-anything-localized-captioning|Describe Anything: Detailed Localized Image and Video Captioning]] — focal prompt + localized vision backbone for SOTA detailed region captioning in images and videos; introduces DLC-SDP and DLC-Bench
- [[papers/2025-skip-newline-reduce-hallucination|SKIP \\N: A Simple Method to Reduce Hallucination in Large Vision-Language Models]] — prompt engineering approach reducing hallucinations by minimizing newline sequences in LLM responses
- [[papers/2025-latent-space-steering-reduce-hallucinations|Reducing Hallucinations in Vision-Language Models via Latent Space Steering]] — visual and textual intervention (VTI) via precomputed feature steering vectors to reduce hallucinations
- [[papers/2025-llamav-o1-step-by-step-reasoning|LlamaV-o1: Rethinking Step-by-step Visual Reasoning in LLMs]] — VLM with explicit step-by-step reasoning for complex visual understanding tasks
- [[papers/2025-internvl-large-vision-language-model|InternVL: A Scalable Vision-Language Model]] — large-scale VLM with strong performance across diverse vision-language benchmarks
- [[papers/2025-mmlongbench|MMLongBench: Benchmarking Long-Context Vision-Language Models Effectively and Thoroughly]] — comprehensive benchmark for evaluating long-context VLMs across 7 dimensions and 12 tasks; exposes significant gaps in handling extended visual-textual inputs

### 2024
- [[papers/2024-intro-vision-language-modeling|An Introduction to Vision-Language Modeling]] — comprehensive introduction to VLM architectures, training paradigms, and applications
- [[papers/2024-florence2-unified-vision-tasks|Florence-2: Advancing a Unified Representation for a Variety of Vision Tasks]] — unified vision model handling classification, detection, segmentation, captioning, grounding, and multimodal tasks
- [[papers/2024-glamm-pixel-grounding-multimodal|GLaMM: Pixel Grounding Large Multimodal Model]] — VLM for pixel-level grounding enabling segmentation, region captioning, phrase grounding, and grounded conversation
- [[papers/2024-lisa-reasoning-segmentation|LISA: Reasoning Segmentation via Large Language Model]] — LLM-based segmentation using embedding-as-mask paradigm for reasoning-based semantic segmentation
- [[papers/2024-llm-seg-bridging-segmentation-language|LLM-Seg: Bridging Image Segmentation and Large Language Model Reasoning]] — LLM-guided segmentation via SAM/DINOv2 mask proposals with LLaVA selection; LLM-Seg40K dataset
- [[papers/2024-seagull-image-quality-assessment-roi|SEAGULL: No-reference Image Quality Assessment for Regions of Interest via Vision-Language Instruction Tuning]] — region-level image quality assessment for blur, distortion, and perceptual importance
- [[papers/2024-bioclip-vision-foundation-tree-of-life|BioCLIP: A Vision Foundation Model for the Tree of Life]] — CLIP finetuned for biological species; TreeOfLife-10M dataset with 10.4M images and 454K species
- [[papers/2024-genartist-multimodal-llm-generation-editing|GenArtist: Multimodal LLM as an Agent for Unified Image Generation and Editing]] — agentic MLLM for image generation, editing, and self-correction
- [[papers/2024-bodyshapegpt-3d-body-shape-manipulation|BodyShapeGPT: SMPL Body Shape Manipulation with LLMs]] — LLM-based manipulation of 3D body shape models

### 2023
- [[papers/2023-improved-llava-visual-instruction-tuning|Improved Baselines with Visual Instruction Tuning]] — LLaVA-1.5: systematic study of LMM design choices; MLP connector, higher resolution, academic task data
- [[papers/2023-gill-generating-images-multimodal|Generating Images with Multimodal Language Models]] — GILL: frozen LLM + image encoder/decoder via learned mapping; retrieval + generation + dialogue
- [[papers/2023-nextgpt-any-to-any-multimodal|NExT-GPT: Any-to-Any Multimodal LLM]] — any-to-any modality support (text, image, video, audio) with modality-switching instruction tuning
- [[papers/2023-imagebind-llm-multimodality-instruction-tuning|ImageBind-LLM: Multi-modality Instruction Tuning]] — instruction-tuned multimodal LLM built on ImageBind embeddings
- [[papers/2023-imagebind-one-embedding-space|ImageBind: One Embedding Space To Bind Them All]] — unified embedding space for images, videos, text, audio, depth, thermal, egocentric video
- [[papers/2023-vision-language-models-vision-tasks-survey|Vision-Language Models for Vision Tasks: A Survey]] — comprehensive survey of VLM training paradigms, downstream tasks, and benchmark performance

### 2021
- [[papers/2021-clipcap-clip-prefix-image-captioning|ClipCap: CLIP Prefix for Image Captioning]] — lightweight image captioning via CLIP encoding → learned prefix → frozen GPT-2; parameter-efficient training

## Concepts

- [[concepts/focal-prompt|Focal Prompt]] — ROI encoding that balances local token density with global context via cross-attention
- [[concepts/detailed-localized-captioning|Detailed Localized Captioning (DLC)]] — multi-granularity region description task, benchmark, and dataset landscape
- [[concepts/semi-supervised-data-pipeline|Semi-Supervised Data Pipeline]] — bootstrapping large-scale caption data from existing annotations + unlabeled images
- [[concepts/long-context-vision-language-models|Long-Context Vision-Language Models (LCVLMs)]] — VLMs processing hundreds of images and thousands of interleaved text tokens
- [[concepts/cross-modal-tokenization|Cross-Modal Tokenization]] — standardized method for counting vision patches and text tokens together
- [[concepts/instruction-tuning|Instruction Tuning]] — adapting LLMs to follow natural language instructions via example-based finetuning
- [[concepts/multimodal-generation|Multimodal Generation]] — LLM-based generation of images, video, audio, and 3D outputs
- [[concepts/hallucination-reduction|Hallucination Reduction]] — techniques to minimize false or unsupported outputs in vision-language reasoning
- [[concepts/parameter-efficient-adaptation|Parameter-Efficient Adaptation]] — training methods (prefix-tuning, adapters, LoRA) for efficient LLM/VLM finetuning

## See also

- [[../agentic-mllms/index|Agentic Multimodal LLMs]] — LLMs orchestrating tools and modules for compositional reasoning
- [[../3d-scene-understanding/index|3D Scene Understanding]] — LLMs applied to point clouds for structured indoor reconstruction
