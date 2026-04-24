---
topic: claim-relation-classification
tags: [concept, method]
---

## Definition

**Scientific claim extraction** is the task of identifying and extracting central, empirically testable assertions from research papers. A scientific claim is defined as a statement about methods, data, or phenomena that a paper advances as a key contribution. Claims differ from definitions, background statements, or incidental observations by being testable and central to the paper's argumentative structure.

## Origins

Scientific claim extraction emerged from work in:
- **Argument mining** (Al Khatib et al., 2021; Binder et al., 2022) — extracting argumentative components from documents
- **Scientific fact verification** (Wadden et al., 2020, 2025) — identifying and verifying scientific assertions
- **Scholarly document understanding** (Li et al., 2022) — extracting key structured information from research papers

ClaimFlow uses claim extraction as an upstream component, building on Pramanick et al. (2025) for automatic identification at scale.

## Key variants / extensions

- **Sentence-level claim extraction** — identifies claim-expressing sentences (used in ClaimFlow)
- **Span-level claim extraction** — identifies minimal claim-containing spans within sentences
- **Claim canonicalization** — groups multiple textual realizations of the same underlying claim
- **Coupled extraction** — jointly extracts claims and evidence supporting them

## Papers using this concept

- [[2026-claimflow-claim-relation-classification|ClaimFlow]] — fine-tunes SciBERT for sentence-level claim identification, achieving 0.79 F1 on the test set; applies it to automatically identify claims in ~13k papers
