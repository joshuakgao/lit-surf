---
title: "TimeSearch-R: Adaptive Temporal Search for Long-Form Video Understanding via Self-Verification Reinforcement Learning"
authors: Pan, Junwen; Zhang, Qizhe; Zhang, Rui; Lu, Ming; Wan, Xin; Zhang, Yuan; Liu, Chang; She, Qi
year: 2025
venue: arXiv:2511.05489 (preprint, under review)
affiliations: ByteDance, School of Computer Science Peking University
topic: video-understanding
source: "[[raw/video-understanding/2025/2025-timesearch-r-temporal-search-video-understanding.pdf]]"
thumbnail: "[[raw/video-understanding/2025/thumbnails/2025-timesearch-r-temporal-search-video-understanding.png]]"
tags:
  - video-understanding
  - temporal-search
  - reinforcement-learning
  - grpo
  - vlm
  - long-form-video
  - rl-reasoning
---

![](/raw/video-understanding/2025/thumbnails/2025-timesearch-r-temporal-search-video-understanding.png)

## Summary

Long-form video understanding requires a model to navigate thousands of frames to identify the minimal set relevant to a question. Prior VLMs rely on static frame sampling — selecting a fixed set of frames before reasoning begins — which is both inefficient and brittle. VideoAgent-style approaches use LLMs as interactive agents with hand-crafted retrieval workflows, but lack end-to-end optimisation for learning *when* to search and *what* to look for.

TimeSearch-R reformulates temporal search as an interleaved text-video thinking process trained via reinforcement learning. The model alternates between textual reasoning (`<think>`) and calling a search tool that retrieves new video frames, progressively narrowing its temporal window before committing to a final answer. A novel RL algorithm, **GRPO-CSV**, extends standard GRPO with a Completeness Self-Verification phase that provides supervision on both successful and failed search trajectories, improving training stability and search completeness.

## Key contributions

- **TimeSearch-R framework**: temporal search as a multi-turn thinking process; the model emits `<tool_call>` instructions to a search function mid-reasoning, interleaving visual evidence acquisition with textual logic
- **GRPO-CSV**: extends GRPO by adding a CSV rollout phase that re-prompts the model to answer using only its gathered frames, generating a completeness reward independent of trajectory length — provides learning signal even when the search fails
- **"Thinking with Videos" paradigm**: distinct from prior RL-for-reasoning work (DeepSeek-R1, Video-R1) which apply GRPO to text-only chains or static image grids; TimeSearch-R is the first to integrate dynamic frame retrieval into the RL reasoning loop
- **Two-stage training data pipeline**: filters long-video QA pairs for (1) visual dependency (question must require video, not just text knowledge) and (2) search usefulness (increasing frames from 4→64 must improve accuracy), yielding high-quality temporal reasoning training data
- SOTA on Haystack-LVBench, Haystack-Ego4D, VideoMME, and LongVideoBench

## Architecture

![[raw/video-understanding/2025/assets/timesearch-fig1-paradigms-and-interleaved-thinking.png]]
*Figure 1: (a) Prior static sampling paradigms vs. TimeSearch-R's adaptive search. (b) Interleaved text-video thinking — model alternates between reasoning and visual search calls*

**Base model:** Qwen2.5-VL-7B-Instruct

**Search function:** Given a temporal window $[t_s, t_e]$ and query $q$, selects $F$ maximally informative frames using Determinantal Point Process (DPP) — balancing query relevance (cosine similarity of visual embeddings to query) with diversity (penalising redundant frames). Frame timestamps are prepended as short text tokens (e.g., `"12.3s"`) before each frame, enabling explicit temporal grounding.

**Interaction loop:** Max 8 search turns per question, max 256 frame tokens per turn, max 768 frames total per video. Model emits `<tool_call>{function-name, arguments}</tool_call>` JSON; environment returns selected frames; model continues reasoning.

**GRPO-CSV training:**

![[raw/video-understanding/2025/assets/timesearch-fig3-grpo-csv-pipeline.png]]
*Figure 3: GRPO (top) vs. GRPO-CSV (bottom) — CSV phase re-answers using only gathered frames, generating a completeness reward*

Three reward components:
- **Format reward** ($R_f$): correct `<think>...</think><answer>...</answer>` trajectory structure
- **Accuracy reward** ($R_{acc}$): binary answer correctness (MC: exact match; open-ended: LLM-as-judge via GPT-4o)
- **Completeness reward** ($R_{comp}$): from CSV phase — measures whether gathered frames alone suffice to answer correctly, independent of trajectory; applied only when format and accuracy rewards are already positive

**Overall reward:** $R = R_f + R_{acc} + R_{comp}$

## Training data

Dataset sourced from: Haystack-Ego4D (49.5%), Panda-70M/VideoMarathon (35.6%), CinePile (9.5%), Others (5.4%). Mean video duration: 1,659 seconds. Question types: 60.3% open-ended, 39.7% multiple-choice.

Two-stage filtering:
1. **Visual dependency**: 4 uniformly sampled frames; if answerable without video content → discard
2. **Search usefulness**: increase to 64 frames; if accuracy doesn't improve → discard (question has weak temporal dependency)

## Results

**Temporal search (Haystack-LVBench):**

| Method | P | R | F₁ | Comp. | Acc. |
|--------|---|---|----|-------|------|
| Qwen2.5-VL w/ search | 0 | 0 | 0 | 44.2 | 59.4 |
| SFT | 1.4 | 4.5 | 2.2 | 56.0 | 72.0 |
| TimeSearch-R (Ours) | **5.4** | **8.4** | **6.4** | **63.8** | **81.0** |

**Long-form video understanding (VideoMME / LongVideoBench):**

| Method | VideoMME | LongVideoBench |
|--------|----------|----------------|
| Qwen2.5-VL-7B (base) | 68.4 | 56.4 |
| Video-R1 | 59.9 | 58.1 |
| TimeSearch-R | **71.5** | **60.1** |

**End-to-end latency (Haystack-Ego4D, A100):** 13.4s vs. VideoAgent 34.9s, T* 33.8s

![[raw/video-understanding/2025/assets/timesearch-fig4-ablation-results.png]]
*Figure 4: Ablation — removing CSV collapses completeness and RL training stability; GRPO-CSV achieves best overall performance*

Key ablation findings:
- Removing CSV: completeness drops from 60.5% → 57.2%, training collapses around step 300
- RL alone (without SFT warm-up): adequate for temporal search, critical for long-video tasks
- GRPO-CSV with accuracy reward achieves best QA performance (66.6%)
- Data composition: including egocentric (Ego4D) data improves temporal (+7.4%) and action reasoning (+5.7%) significantly

## Relation to prior work

- **VideoAgent** (Wang et al., 2024): LLM-based interactive video agent with handcrafted tool workflows; TimeSearch-R surpasses it while achieving 2.6× lower latency and learning search strategies end-to-end rather than through engineered pipelines
- **T*** (Ye et al., 2025): Prior SOTA on Haystack benchmarks using detector-based frame retrieval; TimeSearch-R surpasses F₁ by 2.5× and QA accuracy by 25+ points on Ego4D
- **Video-R1** (Feng et al., 2025): Applies GRPO to video reasoning but with static frame sampling; TimeSearch-R adds adaptive search and outperforms it on all benchmarks including a +11.6% gap on VideoMME
- **DeepSeek-R1**: Motivates the RL-for-reasoning paradigm; TimeSearch-R extends it to the dynamic visual domain where reasoning must interleave with active perception

## Open questions / limitations

- Evaluated only on QA benchmarks; temporal grounding (localisation) precision for open-ended events remains unmeasured
- CSV reward requires an additional LLM forward pass per rollout, increasing training compute
- Max 768 frames per video limits applicability to very long content (>3 hours) without further hierarchical search
- Search function is not learned — DPP is a fixed heuristic; end-to-end learned retrieval could yield further gains
- LLM usage disclaimer: authors note LLMs were used for writing polish/fluency only, not for literature review or experimental analysis
