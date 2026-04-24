---
topic: claim-extraction
tags: [concept, metric]
---

## Definition

**Element-level coverage** is a fine-grained evaluation metric for claim extraction that assesses whether extracted claims capture distinct pieces of information (verifiable elements) from the source text.

Rather than evaluating coverage at the sentence level (did the method correctly identify that a sentence contains a claim?), element-level coverage breaks sentences into distinct information units and evaluates coverage for each unit separately.

**Classification**:
- **True positive**: verifiable element covered explicitly or implicitly by extracted claims
- **False negative**: verifiable element not covered
- **True negative**: unverifiable element not covered (or only implicitly covered)
- **False positive**: unverifiable element explicitly covered

## Origins

Prior work on claim extraction primarily evaluated coverage at the **sentence level** — binary classification of whether a sentence contains a factual claim (Konstantinovskiy et al., 2021; Majer & Šnajder, 2024).

Some recent work approached element-level granularity (Song et al., 2024; Li et al., 2024) but relied on human annotation, lacked specificity in quantifying omissions, failed to penalize inclusion of unverifiable content, or didn't distinguish between implicit and explicit coverage.

## Key variants / extensions

**Implicit vs. explicit coverage**: Element-level coverage distinguishes between:
- **Explicit coverage**: element is directly stated in extracted claims
- **Implicit coverage**: element is suggested or entailed by extracted claims

Implicit coverage of verifiable elements is treated as true positive (claim captures the meaning), while implicit coverage of unverifiable elements is not treated as true positive (may not reflect deliberate inclusion).

**Example** (from Claimify):
- Sentence: "The iconic American flag has 50 stars and 13 stripes"
- Elements: (1) flag is iconic [unverifiable], (2) flag has 50 stars [verifiable], (3) flag has 13 stripes [verifiable]
- Method A extracts: ["flag is iconic", "flag has numerous stars and stripes"] → 1 false positive, 2 false negatives
- Method B extracts: ["flag contains 50 stars", "flag contains 13 stripes"] → 0 false positives, 2 true positives
- Element-level metric correctly identifies Method B as superior

## Papers using this concept

- [[2025-claimify-claim-extraction|Claimify]] — introduces automated element-level coverage evaluation with granular assessment of verifiable elements and distinction between implicit/explicit coverage
