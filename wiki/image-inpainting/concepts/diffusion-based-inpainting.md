---
topic: image-inpainting
tags: [concept, method]
---

## Definition

Diffusion-based inpainting leverages denoising diffusion probabilistic models (DDPMs) or latent diffusion models (LDMs) for image inpainting. The approach exploits the powerful semantic priors learned by pre-trained diffusion models through iterative denoising. During inference, the model alternates between: (1) generating noisy content for masked regions via diffusion reversal, and (2) replacing unmasked regions with the known image to preserve context. This sampling-based approach requires no task-specific training and generalizes across arbitrary mask distributions.

## Origins

While diffusion models were early explored for inpainting (Sohl-Dickstein et al., Song et al., pre-2022), [[2022-repaint-inpainting-diffusion|RePaint]] was first to demonstrate practical state-of-the-art results using pre-trained unconditional DDPMs, establishing diffusion as the dominant paradigm in modern inpainting.

## Key variants / extensions

- **Mask-based conditioning**: Replace unmasked regions during sampling (RePaint, Uni-paint)
- **Attention-based conditioning**: Use attention mechanisms to enforce mask constraints (CorrFill, SmartBrush)
- **Text-conditioned diffusion**: Text-to-image models adapted for inpainting via fine-tuning (Stable Inpainting, SmartBrush)
- **Few-shot diffusion**: Fine-tune on single images without large datasets (Uni-paint)
- **Repainting strategies**: Forward-backward iterations for semantic refinement (RePaint)

## Papers using this concept

- [[2022-repaint-inpainting-diffusion]] — Foundational training-free diffusion inpainting with repainting strategy
- [[2022-smartbrush-text-shape-guided-inpainting]] — Text-to-image diffusion adapted for guided inpainting
- [[2023-unipaint-multimodal-inpainting]] — Few-shot fine-tuning of diffusion for multimodal inpainting
- [[2025-corrfill-reference-based-inpainting]] — Attention-guided diffusion with correspondence constraints
