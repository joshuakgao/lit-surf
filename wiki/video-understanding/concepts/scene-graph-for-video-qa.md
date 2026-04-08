---
topic: video-understanding
tags: [concept, method, scene-graph, spatial-reasoning]
---

## Definition

A **scene graph** is a structured representation of a visual scene encoding objects (nodes) and their pairwise relationships (edges) — e.g., `[player] → [passing] → [ball]`. In video QA, scene graphs provide explicit spatial and relational context that frame-level embeddings alone cannot reliably capture, particularly in crowded scenes with multiple actors or fine-grained relationship queries.

## Why scene graphs help video QA

Standard video-language models encode visual content as patch embeddings from a ViT, which captures appearance but implicitly represents relationships. For questions requiring precise spatial reasoning — *"What is player A doing relative to player B?"* — the model must infer entity relationships from distributed attention patterns. Scene graphs make these relationships explicit and directly encodable as language tokens.

Key failure mode without scene graphs: in multi-actor videos, models misattribute actions to the wrong entity when asked about a specific person. SGVLM's ablations show SGVLM without scene graph predictor (SGVLM$_{SG_{det}}$) shows pronounced degradation on relationship questions specifically.

## Integration in SGVLM

SGVLM (Dai et al., 2025) integrates scene graphs as follows:
1. **Predict:** Neural Motifs backbone predicts bounding boxes $B$, object classes $O$, and label probabilities $\mathbf{p}_b$ for each frame
2. **Encode:** Q-Former + LLM encodes each object's context into scene graph token embeddings $\mathbf{S}$
3. **Fuse:** $\mathbf{S}$ is concatenated with frame tokens $\mathbf{X}_v$ and passed to the main LLM alongside question tokens

The scene graph predictor is pre-trained on Visual Genome and fine-tuned on MOMA-QA. At inference, it runs on the top-$k$ localised frames (not all frames), keeping compute tractable.

## Relation to 3D scene graphs

The concept is closely related to structured scene representations in 3D understanding (see [[../../3d-scene-understanding/concepts/structured-scene-representation|Structured Scene Representation]]). SpatialLM predicts 3D object bounding boxes and layout as structured text; SGVLM predicts 2D scene graphs per frame. Both represent a shift from implicit (embedding-based) to explicit (symbolic) scene structure.

## Papers using this concept

- [[papers/2025-moma-qa-fine-grained-video-question-answering|MOMA-QA / SGVLM (Dai et al., 2025)]] — scene graph predictor (Neural Motifs + Q-Former) integrated into video-language pipeline; critical for relationship-type questions in multi-actor scenarios
