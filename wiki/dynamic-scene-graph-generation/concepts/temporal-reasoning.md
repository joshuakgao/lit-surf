---
topic: dynamic-scene-graph-generation
tags: [concept, method]
---

## Definition

Temporal reasoning refers to modeling and inference over time-dependent information and relationships. In dynamic scene graph generation, it involves understanding how object relationships and interactions change across video frames, including the duration, sequence, and dependencies of events.

## Origins

Temporal reasoning in vision emerged from action recognition and video understanding tasks. In scene graph generation, it extends static spatial reasoning to capture how relationships evolve—e.g., from "person touches bottle" to "person holds bottle to mouth" to "person drinks from bottle".

## Key variants / extensions

- **Frame-level temporal reasoning**: Modeling relationships between adjacent or nearby frames
- **Sequence-level temporal reasoning**: Capturing longer-range temporal dependencies and activity structure
- **Hierarchical temporal reasoning**: Decomposing complex activities into constituent sub-actions and micro-interactions
- **Causal temporal reasoning**: Inferring temporal causality and predictive relationships between events

## Papers using this concept

- [[../papers/2021-spatial-temporal-transformer-dynamic-scene-graph|STTran (2021)]] — Uses transformer decoder to model temporal dependencies across frames for relationship prediction
