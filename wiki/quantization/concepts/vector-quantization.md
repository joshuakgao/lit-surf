---
topic: quantization
tags: [concept, method]
---

## Definition

Vector quantization (VQ) is the process of mapping high-dimensional continuous vectors to discrete codewords from a finite codebook. The goal is to minimize distortion—typically measured by mean-squared error (MSE) or inner product error—while reducing the number of bits required to represent each vector. VQ preserves geometric properties of the original vector space necessary for downstream tasks.

## Origins

Vector quantization has roots in Shannon's source coding theory, formalized through the distortion-rate function. Lloyd-Max quantization (1957) established optimal scalar quantization principles. Product quantization (PQ) extended these ideas to high-dimensional vectors by quantizing subspaces independently.

## Key variants / extensions

- **Scalar quantization**: Quantizing individual coordinates independently
- **Product quantization (PQ)**: Dividing vectors into subspaces and quantizing each subspace with a separate codebook
- **Vector quantization with structure**: Leveraging special structure (rotation, clustering) to improve codebook design
- **Online vector quantization**: Data-oblivious quantization suitable for streaming applications (e.g., KV cache during inference)

## Papers using this concept

- [[../papers/2025-turboquant-online-vector-quantization|TurboQuant (2025)]] — Achieves near-optimal vector quantization through random rotation and per-coordinate Lloyd-Max quantization, with unbiased inner product preservation
