# Image Inpainting — Index

Image inpainting is the task of filling missing or corrupted image regions in a way that appears natural and semantically coherent. This wiki tracks literature on diffusion-based inpainting methods, which have emerged as the dominant paradigm through their ability to leverage pre-trained generative priors. Coverage includes unconditional inpainting, text-guided approaches, reference-based methods, and multimodal guidance combining spatial and semantic controls.

## Papers by year

### 2025
- [[papers/2025-corrfill-reference-based-inpainting|CorrFill: Enhancing Faithfulness in Reference-based Inpainting with Correspondence Guidance]] — Training-free correspondence-guided module for reference-based inpainting, ensuring geometric correlation preservation

### 2023
- [[papers/2023-unipaint-multimodal-inpainting|Uni-paint: A Unified Framework for Multimodal Image Inpainting]] — First unified framework supporting unconditional, text, stroke, exemplar, and mixed-mode inpainting with few-shot finetuning

### 2022
- [[papers/2022-repaint-inpainting-diffusion|RePaint: Inpainting using Denoising Diffusion Probabilistic Models]] — Foundational diffusion-based approach using pre-trained DDPMs with repainting strategy, generalizes to arbitrary masks
- [[papers/2022-smartbrush-text-shape-guided-inpainting|SmartBrush: Text and Shape Guided Object Inpainting]] — Combines text and shape guidance with precision control and background preservation via foreground mask prediction

## Concepts
- [[concepts/image-inpainting|Image Inpainting]] — Task of filling missing/corrupted image regions
- [[concepts/diffusion-based-inpainting|Diffusion-Based Inpainting]] — Using diffusion models as generative priors for inpainting
- [[concepts/multimodal-guidance|Multimodal Guidance]] — Combining multiple guidance modalities (text, spatial, exemplars)

## See also
- [[../depth-estimation/index|Depth Estimation]] — Related dense prediction task
- [[../denoising-segmentations/index|Denoising Segmentations]] — Related to image quality improvement
