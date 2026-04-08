---
topic: video-understanding
tags: [concept, efficiency, method]
---

## Definition

Vision token pruning is a technique to reduce computational overhead in vision-language models by selectively removing or merging visual tokens (encoded features from video frames) before processing by the LLM backbone. The goal is to decrease sequence length and thus reduce LLM inference cost while preserving task performance.

## Origins

Token pruning emerged from the observation that long-form videos generate very long token sequences (>10,000 tokens for minute-long videos). Early approaches indiscriminately pruned low-magnitude tokens or merged similar tokens (ToMe, Token Merging). The key challenge is that naive pruning loses spatio-temporal structure. More sophisticated variants introduced in 2025 use query-awareness or learned relevance prediction to make pruning decisions.

## Key variants / extensions

- **Magnitude-based pruning**: remove tokens with lowest activation magnitudes; simplest but doesn't account for task relevance
- **Similarity-based merging (ToMe)**: merge similar tokens; preserves more structure than magnitude pruning but ignores semantic importance
- **Query-aware adaptive pruning (KVTP)**: assign per-frame pruning rates based on query-frame relevance; frame-level decision making
- **Token-level vs. frame-level pruning**: pruning individual tokens (fine-grained, high flexibility) vs. pruning all tokens of a frame uniformly (coarse-grained, simpler)

## Papers using this concept

- [[2025-keyframe-oriented-vision-token-pruning|Keyframe-oriented Vision Token Pruning (2025)]] — combines keyframe selection with adaptive token pruning via query-aware relevance prediction; achieves 80% token reduction; introduces SparseKV-QA benchmark
- [[2025-re-thinking-temporal-search-long-form-video|Re-thinking Temporal Search (2025)]] — frames temporal search as spatial search; orthogonal efficiency approach to direct token pruning
