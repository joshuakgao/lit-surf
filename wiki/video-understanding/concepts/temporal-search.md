---
topic: video-understanding
tags: [concept, method, retrieval, video]
---

## Definition

**Temporal search** is the task of identifying a minimal, maximally informative subset of frames from a long video that is sufficient to answer a specific query. Unlike static frame sampling (uniform, keyframe, or random), temporal search is *query-dependent* and *iterative* — the selected frames depend on both the video content and the question being asked, and the selection can be refined across multiple rounds.

## The core problem

Long-form videos (minutes to hours) contain thousands of frames. A model given all frames simultaneously would exceed context limits and attend poorly to relevant moments. A model given only a few uniformly sampled frames will miss critical content. Temporal search resolves this by narrowing the temporal window to where the answer-relevant content is.

## Approaches

**Static sampling (baseline):** Select $k$ frames uniformly or by keyframe detection before reasoning begins. Simple but ignores the query entirely and cannot refine selection based on partial evidence.

**Retrieval-augmented generation (e.g., VRAG):** Explicitly separates retrieval from reasoning. A multimodal search system (semantic embeddings, audio, OCR, object detection) retrieves candidate segments; a re-ranking stage incorporates temporal context and refines candidates; answer generation then operates only on top-K segments. Training-free; naturally handles multimodal queries; clean separation of concerns. May miss rare or subtle content if initial retrieval fails.

**Agent-based retrieval (e.g., VideoAgent):** An LLM orchestrates tool calls to a retrieval function, using handcrafted workflows. Effective but not end-to-end optimised; latency is high due to multi-step orchestration.

**Spatial reformulation (e.g., T*):** Reframes temporal search as spatial search by transforming frame sequences into image grids. A spatial search model iteratively detects objects and refines spatial-temporal regions through coarse-to-fine zooming. Inspired by visual search techniques in images (V*); exploits the fact that image-language models outperform video-language models, suggesting the temporal dimension is the true bottleneck. Achieves 3x computational efficiency improvement.

**Language agent-guided classical search (e.g., AKEYS):** Combines off-the-shelf search algorithms (A*, Dijkstra's, BFS/DFS) with language agents that estimate heuristic costs *h(n)* and movement costs *g(n)* at each step. The agent guides node expansion in a hierarchical video tree and determines termination. No training required; leverages agent reasoning directly within classical algorithm frameworks.

**RL-trained adaptive search (e.g., TimeSearch-R):** The model learns optimal temporal search strategies from data via reinforcement learning. Search is formulated as a multi-turn interaction where the model interleaves reasoning with `<tool_call>` instructions, receiving frames and refining its temporal window iteratively. The search policy is learned, not engineered.

**DPP-based frame selection:** Within a temporal window, selects $F$ frames by maximising diversity and query relevance jointly using a Determinantal Point Process. Ensures selected frames are both relevant to the query and non-redundant.

## Emergent search patterns (from TimeSearch-R case studies)

- **Hypothesis-driven search**: forms a hypothesis about likely frame content, searches to confirm or deny it
- **Confirmation/elimination search**: applies multi-choice elimination by searching for frames that rule out wrong options
- **Sequential search**: decomposes temporal ordering tasks into step-by-step frame retrieval following the sequence of events

## Papers using this concept

- [[papers/2024-vrag-retrieval-augmented-video-qa|VRAG (Tran Gia et al., 2024)]] — RAG-based multimodal retrieval (semantic, audio, OCR, objects) + temporal re-ranking for long-form VideoQA; clean separation of retrieval and reasoning; 40.5/45 on KIS, 4/5 on VQA queries
- [[papers/2025-re-thinking-temporal-search-long-form-video|T* (Ye et al., 2025)]] — reframes temporal search as spatial search via image grids; introduces LV-HAYSTACK benchmark (480h, 15,092 instances) revealing 2.1% temporal F1 SOTA gap; achieves 3x FLOPs efficiency and improves GPT-4o 50.5%→53.1%, LLaVA-OV-72B 56.5%→62.4% with 32 frames
- [[papers/2025-agentic-keyframe-search|AKEYS (Fan et al., 2025)]] — agent-guided A*/Dijkstra's search on hierarchical video trees; no training required; achieves 63.1% on EgoSchema and 77.4% on NExT-QA with only 43.5% frame processing of VideoTree
- [[papers/2025-timesearch-r-temporal-search-video-understanding|TimeSearch-R (Pan et al., 2025)]] — RL-trained adaptive temporal search; SOTA on Haystack-LVBench, Haystack-Ego4D, VideoMME, LongVideoBench
