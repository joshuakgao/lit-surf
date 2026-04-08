---
topic: vision-language-models
tags: [concept, task, dense-captioning]
---

## Definition

**Detailed Localized Captioning (DLC)** is the task of generating rich, multi-sentence natural language descriptions of user-specified regions within an image or video frame, capturing fine-grained attributes, spatial relationships, and contextual understanding of that region.

DLC spans three granularities:
- **Keyword-level** — output is a class name or short tag (e.g., "golden retriever")
- **Phrase-level** — output is a short noun phrase with key attributes (e.g., "a fluffy golden dog mid-leap")
- **Detailed** — output is a full multi-sentence description covering appearance, parts, context, and relationships

## Origins

The task formalizes and unifies prior work on referring expression comprehension, dense captioning, and region description. The term DLC and a systematic benchmark (DLC-Bench) were introduced by Lian et al. in 2025 alongside the DAM model.

## Why it's hard

Three key challenges identified in the literature:
1. **Loss of region detail** — cropping the ROI discards surrounding context needed to understand occlusion, scale, and relationships
2. **Scarcity of training data** — no large-scale dataset of high-quality region-level detailed captions existed prior to DLC-SDP
3. **Benchmark limitations** — reference-caption metrics (BLEU, CIDEr, METEOR) penalize correct but differently-worded descriptions; LLM-as-judge approaches (DLC-Bench) are more appropriate

## Evaluation: DLC-Bench

DLC-Bench evaluates model outputs against a set of manually curated positive and negative attribute questions per region (using Objects365 validation set). An LLM judge scores each answer:
- **Positive questions** test for details that *should* be in the description
- **Negative questions** test for hallucinated details that *should not* be present
- Scoring: +1 for correct, 0 for partially correct, penalty for factual errors

## Datasets

| Dataset | Regions | Granularity | Notes |
|---------|---------|-------------|-------|
| IVIS | 373,551 | keyword | Open-class, objects in complex scenes |
| PACO | 81,325 | phrase | Objects + parts |
| Flickr30k Entities | 427,113 | phrase | — |
| Ref-L4 | — | detailed | Multi-sentence reference captions |
| DLC-SDP (DAM) | 1,458,203 | all | Semi-supervised, not public |

## Papers using this concept

- [[papers/2025-describe-anything-localized-captioning|Describe Anything (Lian et al., 2025)]] — introduced DLC-SDP and DLC-Bench; SOTA at all three granularities
