---
topic: quantization
tags: [concept, application]
---

## Definition

KV (key-value) cache quantization compresses the cached embeddings of previously-generated tokens in transformer models. In autoregressive inference, the KV cache grows linearly with context length, becoming a significant memory bottleneck. Quantization reduces cache size (and associated memory bandwidth) while preserving the geometric properties (inner products, distances) necessary for accurate attention computation.

## Origins

Transformer decoder architectures (Vaswani et al., 2017) introduced the KV cache as a fundamental bottleneck for long-context inference. Recent work (2024-2025) applies vector quantization directly to KV embeddings to enable efficient long-context LLM deployment.

## Key variants / extensions

- **Static quantization**: Fixed per-model quantization scheme applied to all KV vectors
- **Dynamic quantization**: Adaptive bit allocation based on token importance or layer depth
- **Multi-bit quantization**: Using different bit-widths for different layers or attention heads
- **Selective quantization**: Quantizing only less-important tokens while keeping critical tokens uncompressed

## Papers using this concept

- [[../papers/2025-turboquant-online-vector-quantization|TurboQuant (2025)]] — Demonstrates 3.5-bit KV cache quantization with zero quality loss and 2.5-bit with minimal degradation on long-context benchmarks
