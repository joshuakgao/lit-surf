---
topic: claim-relation-classification
tags: [concept, relation]
---

## Definition

An **epistemic relation** is the type of scientific engagement between two claims across papers. It captures how a citing paper's claim relates to a cited paper's claim in terms of support, contradiction, extension, or qualification. Epistemic relations are distinguished from rhetorical or functional aspects of citations by explicitly modeling the *content* relationship between claims rather than just their citation context.

## Origins

The taxonomy of epistemic relations in ClaimFlow is grounded in:
- **Argumentation theory** (Toulmin, 2003) — distinguishing different types of argumentative moves
- **Scientific discourse analysis** (Lauscher et al., 2018) — studying how arguments are structured in research communication
- **Citation analysis** traditions that move beyond simple paper-level citations to fine-grained claim-level relationships

The five-relation taxonomy (support, extend, qualify, refute, background) provides a minimal but expressive set for characterizing how scientific ideas evolve and interact.

## Key variants / extensions

- **Citation intent classification** — prior work (Teufel et al., 2006; Cohan et al., 2019) classifies *rhetorical* function (e.g., background use, comparison) rather than *epistemic* content
- **Scientific fact verification** — evaluates whether individual statements are supported by evidence, often within a single document
- **Argument mining** — extracts argument structures from papers but typically treats claims in isolation rather than tracking interactions

ClaimFlow advances beyond these by explicitly modeling claim-level epistemic relations across papers.

## Papers using this concept

- [[2026-claimflow-claim-relation-classification|ClaimFlow]] — introduces the concept and defines the five-relation taxonomy as the core of the Claim Relation Classification task
