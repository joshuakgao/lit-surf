# Quantization — Index

Quantization is the process of reducing the bit-width or precision of numerical representations—vectors, weights, activations—while minimizing information loss. This wiki covers theoretical foundations, algorithms, and applications in model compression, inference optimization, and vector databases. Focus areas include vector quantization, weight quantization, activation quantization, and KV cache compression for efficient deployment of large-scale models.

## Papers by year

### 2025
- [[papers/2025-turboquant-online-vector-quantization|TurboQuant: Online Vector Quantization with Near-optimal Distortion Rate]] — Theoretically-grounded vector quantization with near-optimal MSE and inner product distortion; applications to KV cache and nearest neighbor search
<img src="/raw/quantization/2025/thumbnails/2025-turboquant-online-vector-quantization.png" height="300"/>

## Concepts
- [[concepts/vector-quantization|Vector Quantization]] — Compressing high-dimensional vectors while preserving geometric structure
- [[concepts/kv-cache-quantization|KV Cache Quantization]] — Compression techniques for transformer key/value embeddings
- [[concepts/distortion-rate|Distortion-Rate Theory]] — Information-theoretic bounds on achievable compression

## See also
- [[../depth-estimation/index|Depth Estimation]] — Uses quantization for efficient 3D reconstruction
- [[../vision-language-models/index|Vision-Language Models]] — Deploy with quantization for inference efficiency
