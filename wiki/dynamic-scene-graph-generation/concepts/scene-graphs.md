---
topic: dynamic-scene-graph-generation
tags: [concept, architecture]
---

## Definition

A scene graph is a structured, graph-based representation of an image or video where nodes represent objects and edges represent relationships/interactions between those objects. Each node contains object class information, and each edge contains relationship type information. Scene graphs provide an interpretable, compositional representation that bridges vision and language.

## Origins

The scene graph concept was formalized for image understanding, with applications in image retrieval and visual question answering. Extended to videos as dynamic scene graphs, incorporating temporal reasoning about how relationships evolve across frames.

## Key variants / extensions

- **Static scene graphs**: Single image; spatial relationships only
- **Dynamic scene graphs**: Video sequences; includes temporal relationships and activity decomposition
- **Attributed scene graphs**: Nodes and edges carry richer attribute information beyond class/relationship labels
- **Grounded scene graphs**: Explicitly linked to natural language descriptions or temporal video segments

## Papers using this concept

- [[../papers/2021-spatial-temporal-transformer-dynamic-scene-graph|STTran (2021)]] — Applies structured scene graph generation with temporal extensions to videos
