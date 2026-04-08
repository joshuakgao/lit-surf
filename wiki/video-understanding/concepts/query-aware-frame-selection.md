---
topic: video-understanding
tags: [concept, method, efficiency]
---

## Definition

Query-aware frame selection (or relevance-based frame selection) is the approach of determining which frames are important relative to a specific query, rather than selecting keyframes based on intrinsic visual properties alone. The relevance score is query-dependent: the same frame may be important for one question but irrelevant for another.

## Origins

Emerged in 2025 as video QA systems evolved to handle long-form content. Earlier approaches selected keyframes through shot detection, motion analysis, or scene changes (task-agnostic). Query-aware approaches recognize that task-specific information should drive frame selection. Motivated by human viewing behavior: when answering a specific question about a video, we seek relevant moments, not all "interesting" frames.

## Key variants / extensions

- **Hard selection with soft pruning (KVTP)**: select keyframes and assign per-frame pruning rates; intermediate between binary selection and naive pruning
- **RL-based dynamic search (TimeSearch-R)**: learn to iteratively request frames during reasoning; interleaves search with reasoning
- **Language agent-guided search (AKEYS)**: agents navigate hierarchical video trees using query context; combines classical algorithms (A*, Dijkstra) with language understanding
- **Supervised frame localization (SGVLM)**: predict temporal intervals of relevant content; requires ground-truth supervision

## Papers using this concept

- [[2025-keyframe-oriented-vision-token-pruning|Keyframe-oriented Vision Token Pruning (2025)]] — frame relevance prediction per query; soft pruning rates adapt to query-frame relevance
- [[2025-timesearch-r-temporal-search-video-understanding|TimeSearch-R (2025)]] — RL learns to dynamically request relevant frames during reasoning
- [[2025-agentic-keyframe-search|Agentic Keyframe Search (2025)]] — language agents guide search through video trees for keyframe discovery
