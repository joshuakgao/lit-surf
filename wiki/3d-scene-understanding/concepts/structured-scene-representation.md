---
topic: 3d-scene-understanding
tags: [concept, representation, output-format]
---

## Definition

A **structured scene representation** encodes 3D indoor environments as a set of typed, parameterised elements — architectural layout components (walls, doors, windows) and objects (bounding boxes with class labels and 6-DoF poses) — in a format that is simultaneously machine-parseable and human-readable.

The key design question is: what format to use? Options include:
- **Regression outputs** (learned decoders, task-specific heads) — fast but not generalizable
- **Mesh/voxel representations** — expressive but memory-intensive and hard to edit
- **Structured text / code** — interpretable, editable, compatible with LLMs, directly usable in downstream tools

## Text-as-structure (SpatialLM approach)

SpatialLM (Mao et al., 2025) encodes scenes as attribute lists in a code-like format:

```
# Layout
@data:class: wall, position_x: int, position_y: int, position_z: int, width: int, height: int
@data:class: door, position_x: int, ...

# Objects
@data:class: chair, position_x: int, ..., angle_x: int, angle_y: int, angle_z: int, scale_x: int, ...
```

This format is directly parseable as Python/structured data, editable by humans, and naturally compatible with LLM auto-regressive generation. It avoids any task-specific decoder heads.

## Trade-offs

| Property | Regression heads | Structured text |
|----------|-----------------|-----------------|
| Flexibility | Low (fixed output schema) | High (variable elements) |
| Interpretability | Low | High |
| Editability | None | Direct |
| LLM compatible | No | Yes |
| Speed | Fast | Slower (sequential generation) |
| Accuracy | High (specialised) | Competitive with SOTA |

## Papers using this concept

- [[papers/2025-spatiallm-structured-indoor-modeling|SpatialLM (Mao et al., 2025)]] — structured text for layout + 3D object bounding boxes; SOTA on Structured3D and ScanNet via LLM generation
