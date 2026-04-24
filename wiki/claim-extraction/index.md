# Claim Extraction — Index

This topic covers work on automatically identifying and extracting factual claims from text, with emphasis on applications to fact-checking and verification of LLM-generated content. Claim extraction is the upstream step in decompose-then-verify pipelines, where extracted claims are later independently verified against evidence. Quality of extraction directly impacts fact-checking effectiveness.

## Papers by year

### 2025
- [[papers/2025-claimify-claim-extraction|Towards Effective Extraction and Evaluation of Factual Claims]] — introduces evaluation framework and Claimify method with explicit ambiguity handling
<img src="/raw/claim-extraction/2025/thumbnails/2025-claimify-claim-extraction.png" height="300"/>

## Concepts
- [[concepts/ambiguity-handling|Ambiguity Handling]] — identifying and resolving referential and structural ambiguities in claim extraction
- [[concepts/decontextualization|Decontextualization]] — ensuring claims can be verified independently without additional context
- [[concepts/element-level-coverage|Element-Level Coverage]] — granular evaluation of whether extracted claims capture distinct information units

## See also
- [[../claim-relation-classification/index|Claim Relation Classification]] — downstream task of classifying how claims interact across papers
- [[../scientific-document-understanding/index|Scientific Document Understanding]] — extracting structured information from research papers
