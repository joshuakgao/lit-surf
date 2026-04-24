---
topic: cognitive-ai
tags: [concept, method]
---

## Definition

Learning from first-person, egocentric perspective—the sensory input and experience from an individual's own viewpoint. In developmental contexts, egocentric learning captures what children actually see and hear as they interact with their environment, move through spaces, and engage with objects and people. Contrasts with third-person or adult-centric views that dominate standard datasets (ImageNet, Ego4D, etc.).

## Origins

Grounded in developmental psychology research (Yoshida & Smith, Aslin, Franchak, Kretch, etc.) showing that infant perspective is dramatically different from adults' and changes with development (crawling, walking, reaching). Operationalized computationally in egocentric video datasets: [[../papers/2025-babyview-egocentric-video-dataset|BabyView]] for child egocentric data; Ego4D for adult egocentric data.

## Key variants / extensions

- **Infant/child egocentric**: High vertical field-of-view to capture hands and objects in interaction; dynamic camera motion from head movement
- **Adult egocentric**: Lower hand presence, different interaction patterns, typically outdoor/action-focused
- **Head-mounted camera egocentric**: Fixed to wearer's head; captures head motion and attention via gaze
- **Robot egocentric**: Embodied in robotic systems; captures third-person robot perspective and action-conditioned learning
- **Virtual egocentric**: First-person in simulation; allows controlled manipulation of learning environment

## Papers using this concept

- [[../papers/2025-babyview-egocentric-video-dataset|BabyView]] — argues that egocentric perspective is essential for understanding human learning; provides first large-scale high-resolution egocentric dataset from children
- [[../../world-models/papers/2026-babyzwm-zero-shot-world-models|BabyZWM]] — trains on BabyView egocentric video; demonstrates that learning from child-scale egocentric data enables efficient visual-cognitive abilities

