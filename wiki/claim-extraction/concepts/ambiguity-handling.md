---
topic: claim-extraction
tags: [concept, method]
---

## Definition

**Ambiguity handling** in claim extraction refers to the explicit identification and resolution of ambiguous language that could lead to multiple interpretations of claims. The key innovation is deciding whether to abstain from extraction when ambiguity cannot be resolved.

Two types of ambiguity:
- **Referential ambiguity**: unclear what a word/phrase refers to (e.g., "They will update the policy next year" — what are "they," "the policy," "next year"?)
- **Structural ambiguity**: grammatical structure allows multiple interpretations (e.g., "AI advanced renewable energy and sustainable agriculture at Company A and Company B" — did AI advance both at both companies, or each technology at one company?)

## Origins

Most prior claim extraction methods either:
1. Ignore ambiguity entirely
2. Assume ambiguity is always resolvable from context

Claimify (Metropolitansky & Larson, 2025) is the first method to explicitly identify unresolvable ambiguities and abstain from extraction when confidence in interpretation is low.

## Key variants / extensions

**Resolution criterion**: An ambiguity is considered resolvable if "a group of readers would likely agree on the correct interpretation" given the question and context.

**Handling unresolvable ambiguity**: Rather than producing potentially incorrect claims, the sentence is labeled "Cannot be disambiguated" and excluded from downstream decomposition. This conservative approach avoids generating misleading claims.

**Special case**: Distinguishing between factual claims and unverifiable author interpretations. For example:
- Sentence: "John emphasized the support he received from executives, highlighting the importance of mentorship"
- Ambiguity: Does John highlight the importance of mentorship, or is this the author's interpretation?

**Prevalence in practice**: Across tested LLMs, 2.4-5.4% of sentences labeled "Cannot be disambiguated", indicating that explicit handling is necessary but selective.

## Papers using this concept

- [[2025-claimify-claim-extraction|Claimify]] — introduces disambiguation stage that identifies and resolves ambiguities, abstaining from extraction when confidence is insufficient; unique among claim extraction methods
