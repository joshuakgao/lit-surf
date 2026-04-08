---
topic: vision-language-models
tags: [concept, capability, evaluation]
---

## Definition

Long-context vision-language models (LCVLMs) are VLMs capable of jointly processing hundreds of images and thousands of interleaved text tokens in a single forward pass, enabling reasoning and generation over extended visual-textual sequences. "Long-context" typically refers to context windows of 8K tokens or more (compared to traditional VLMs with 2K–4K windows).

## Origins

Emerged from the success of long-context LLMs (extended context windows via RoPE, ALiBi, Flash Attention) and the practical demand for VLMs to handle multi-page documents, long videos, and complex visual reasoning tasks. Early models (LongVILA, GPT-4o) demonstrated feasibility. MMLongBench (2025) is the first comprehensive benchmark, establishing this as a distinct capability category.

## Key variants / extensions

- **Vision patch tokenization strategies**: how images are encoded into tokens (standard, hierarchical, patch merging); affects context length accounting
- **Vision-text interleaving**: how vision and text tokens are mixed in the sequence; affects reasoning over multimodal information
- **Context length control methods**: techniques to extend context (RoPE extensions, attention optimizations, selective focus)
- **Task-specific long-context use cases**: VRAG (retrieval-augmented), NIAH (needle-in-haystack), ICL (few-shot from examples), document understanding, summarization

## Papers using this concept

- [[2025-mmlongbench|MMLongBench (2025)]] — first comprehensive benchmark for LCVLMs; evaluates 46 models across five task categories (VRAG, NIAH, ICL, Summarization, DocVQA) at standardized lengths 8K–128K tokens; finds task performance is weak proxy for overall capability
