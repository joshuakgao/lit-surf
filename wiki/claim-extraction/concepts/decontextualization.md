---
topic: claim-extraction
tags: [concept, evaluation]
---

## Definition

**Decontextualization** in claim extraction refers to the degree to which an extracted claim can be understood and verified independently, without requiring additional information from its original source text. A decontextualized claim should be self-contained and retain the meaning it held in its original context.

In fact-checking contexts, decontextualization is critical: if a claim omits necessary context, a fact-checking system may retrieve evidence that contradicts the claim's source sentence, leading to incorrect verdicts.

## Origins

The concept appears in prior work on claim extraction, evidence extraction, and natural language inference (Choi et al., 2021; Gunjal and Durrett, 2024). Prior approaches relied on:
- **Subjective human judgment** — annotators assessing whether a claim is "sufficiently" decontextualized (Kane and Schubert, 2023; Bayat et al., 2025)
- **Retrieval-based evaluation** — checking whether retrieval results change based on context (Deng et al., 2024)

These approaches are problematic: subjectivity makes consistency difficult, and retrieval changes don't necessarily affect the final fact-checking verdict.

## Key variants / extensions

**Claimify's outcome-based approach** (Metropolitansky & Larson, 2025):
- Rather than judging whether context is "sufficient," measure whether *missing context affects the fact-checking verdict*
- Three-step process: generate maximally decontextualized version (c_max), retrieve evidence for both versions, check if verdicts align
- Classifies results as desirable (verdicts agree) or undesirable (verdicts disagree)
- Grounds evaluation in fact-checking performance, making it pragmatic and replicable

**Traditional definition**:
1. Claim is understandable on its own
2. Claim retains original meaning in its context

## Papers using this concept

- [[2025-claimify-claim-extraction|Claimify]] — proposes outcome-based decontextualization evaluation where missing context is problematic only if it changes the fact-checking verdict
