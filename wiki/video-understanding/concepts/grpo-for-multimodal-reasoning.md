---
topic: video-understanding
tags: [concept, method, reinforcement-learning, training]
---

## Definition

**Group Relative Policy Optimization (GRPO)** is an RL algorithm for training LLMs that estimates advantages relative to a group of sampled outputs, avoiding the need for a separate value network. It was popularised in DeepSeek-R1 for text reasoning and has since been extended to multimodal and video reasoning tasks.

## Standard GRPO

For a given input $q$, GRPO samples $G$ completions from the policy model, computes rewards $\{r_i\}$, and estimates advantage as $A_i = \frac{r_i - \text{mean}(\{r_j\})}{\text{std}(\{r_j\})}$. The policy is updated to increase probability of high-advantage completions while a KL penalty prevents drift from the reference model.

**Strengths for reasoning:** Outcome-based rewards (answer correctness) are sufficient — no process-level annotation needed. The model learns to self-improve its chain-of-thought by observing which reasoning trajectories yield correct answers.

## GRPO-CSV (Completeness Self-Verification)

Introduced in TimeSearch-R (Pan et al., 2025) to address two failure modes in video RL:

1. **Insufficient temporal exploration**: standard GRPO rewards only the final answer, so the model may short-circuit search after finding a plausible but incomplete frame set
2. **Inconsistent logical reasoning**: the model's intermediate reasoning may contradict its final answer

GRPO-CSV adds a **CSV rollout phase** after multi-turn search:
- The model is prompted to re-answer using only the currently gathered dynamic frame set, without further search
- A **completeness reward** ($R_{comp}$) is computed from this re-answer, measuring whether gathered visual evidence is sufficient for correct reasoning
- CSV reward is applied only when format and accuracy rewards are positive — avoiding noisy gradients from failed trajectories

**Key benefit:** Provides learning signal from both successful and failed search trajectories. Without CSV, RL training collapses around step 300 as the model stops exploring and completeness drops.

## Broader context

GRPO and variants are part of a trend of applying outcome-based RL to improve reasoning in foundation models without expensive process-level supervision:
- DeepSeek-R1 (text reasoning)
- Video-R1 (static video frames + GRPO)
- TimeSearch-R (dynamic video search + GRPO-CSV)
- Spatial reasoning, code generation, and mathematical reasoning tasks all benefit from similar formulations

## Papers using this concept

- [[papers/2025-timesearch-r-temporal-search-video-understanding|TimeSearch-R (Pan et al., 2025)]] — GRPO-CSV for adaptive temporal video search; completeness reward from self-verification prevents training collapse
