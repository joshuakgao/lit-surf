---
topic: quantization
tags: [concept, theory]
---

## Definition

Distortion-rate theory, rooted in Shannon's source coding, characterizes the fundamental trade-off between compression rate (bits per sample) and distortion (information loss). For vector quantization, the distortion-rate function D(R) specifies the minimum achievable distortion at a given bit-rate. Information-theoretic lower bounds establish what no algorithm can do better than.

## Origins

Introduced by Claude Shannon in "A Mathematical Theory of Communication" (1948). Formalizes the limits of lossless and lossy compression. Applied to vector quantization by establishing optimal codebook design principles.

## Key variants / extensions

- **MSE-based distortion-rate**: Minimizing mean-squared error; achievable through Lloyd-Max quantization and variants
- **Semantic distortion-rate**: Minimizing task-specific loss rather than geometric error (e.g., inner product error for retrieval)
- **Constrained distortion-rate**: Subject to computational, memory, or latency constraints
- **Multi-objective distortion-rate**: Balancing multiple distortion metrics simultaneously

## Papers using this concept

- [[../papers/2025-turboquant-online-vector-quantization|TurboQuant (2025)]] — Provides formal information-theoretic lower bounds and proves near-optimal distortion rates within ~2.7× factor for both MSE and inner product distortion
