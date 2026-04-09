---
topic: world-models
---

# World Models — Overview

*Last updated: 2026-04-09 | Sources: 2 papers*

## Current thesis

World models emerge from video through two complementary mechanisms: **self-supervised learning of physics** and **systematic evaluation of reasoning**. V-JEPA (2025) demonstrates that intuitive physics understanding emerges spontaneously from masked video prediction in representation space—no explicit labels needed. VBVR (2026) provides the first large-scale benchmark to measure what world reasoning capabilities exist and how they scale. Together, these papers suggest: (1) representation-space prediction is a sufficient inductive bias to acquire physics understanding, and (2) systematic evaluation of diverse reasoning tasks reveals emergent generalization to unseen task types. World models are learnable and measurable at scale.

## Key trends

**2025:**
- **Representation-space prediction as world modeling paradigm**: V-JEPA shows that prediction in learned space (not pixels) is the right inductive bias for physics. This bridges structured models (which use hand-coded 3D) and pixel-based models (which fail), offering a principled middle ground.
- **Emergent physics from self-supervised learning**: No physics labels, no task-specific training—just masked video prediction. Physics understanding emerges as a byproduct of learning to model video. Challenges "core knowledge" hypothesis and supports learned emergence.
- **Violation-of-expectation as universal probe**: Adapting developmental psychology's surprise metric enables zero-shot physics probing without task-specific adaptation. "Surprise" (prediction error) directly measures whether a model's world model expects observed events.
- **Minimal data sufficiency**: Physics understanding achieves above-chance accuracy with as little as one week of video. Suggests physics reasoning is a learnable signal accessible at modest data scales, not requiring massive pretraining.
- **Alignment with predictive coding neuroscience**: Results align with neuroscience theories (Rao & Ballard, Hohwy) that brains learn by minimizing prediction error. V-JEPA provides a computational instantiation of predictive coding for vision.

**2026:**
- **Large-scale benchmarks for world reasoning**: VBVR introduces 2.015M samples—1000× larger than prior benchmarks. Enables first reproducible scaling studies of world reasoning across five cognitive capabilities.
- **Cognitive science grounding**: VBVR anchors task taxonomy in foundational faculties (Spatiality, Transformation, Knowledge, Abstraction, Perception) rather than ad-hoc task selection.
- **Verifiable evaluation paradigm**: VBVR-Bench uses rule-based, human-aligned scorers instead of VLM judges. Enables reproducible, interpretable diagnosis of specific reasoning bottlenecks.
- **Emergent generalization in world reasoning**: VBVR's scaling study reveals that models improve on unseen task types with more training data—suggesting world reasoning capabilities generalize systematically, not just memorize.
- **Integration of physics and task reasoning**: V-JEPA's emergent physics and VBVR's task-based benchmarks represent complementary approaches to understanding world models—mechanism vs. measurement.

## Open problems

**Physics learning (V-JEPA):**
- **Real-world physics complexity**: IntPhys tests synthetic object trajectories; whether models capture complex real-world physics (soft bodies, friction, fluids, deformables) remains unexplored
- **Long-horizon prediction**: Current work focuses on short-term prediction (next few frames); whether models acquire stable physics models over extended horizons (>1 minute) is unclear
- **Counterfactual reasoning**: Current framework is passive (detecting violations); active reasoning—generating "what if?" scenarios—is not addressed
- **Semantic grounding**: Models learn visual physics but do not integrate semantic understanding (categories, materials, agents); fusion of physics and semantics is open
- **Scaling laws**: Study uses modest models; whether scaling to larger architectures reveals new physics behaviors is unknown
- **Integration with action**: Models are observation-only; learning action-conditioned world models (robotics, RL) is a critical frontier
- **Implicit vs. explicit physics**: Do learned representations capture explicit constraints (e.g., Lagrangian mechanics) or only implicit patterns? Interpretability remains open

**World reasoning benchmarks (VBVR):**
- **Real-world generalization**: VBVR tasks are curated/synthetic; robustness on in-the-wild video reasoning not extensively evaluated
- **Long-horizon reasoning**: Tasks emphasize short-range reasoning; multi-step causal chains over extended video remain underexplored
- **Model architecture diversity**: Scaling study focuses on generation models; how discriminative and other architectures scale is open
- **Task distribution bias**: Despite community contribution, coverage may be uneven; some capabilities may have fewer exemplars
- **Extrapolation beyond 2M**: Do scaling trends continue to 10B+ samples? Classical scaling law assumptions may not hold

**Integration:**
- **Physics ↔ Task reasoning**: Can V-JEPA's physics improve VBVR task performance? Do task-trained models develop emergent physics?
- **Joint evaluation**: No existing benchmark that simultaneously measures physics understanding and task reasoning

## Contradictions and debates

- **Core knowledge vs. learned emergence**: Traditional developmental psychology argues physics is innate ("core knowledge"). V-JEPA's success suggests learned emergence, but may reflect specific inductive biases of the architecture rather than true "learning from scratch."

## Recommended reading order

1. [[papers/2025-intuitive-physics-self-supervised-pretraining|V-JEPA Intuitive Physics (2025)]] — establishes that representation-space prediction learns physics without explicit supervision; entry point for understanding emergent world models from self-supervised learning
2. [[papers/2026-vbvr-very-big-video-reasoning|VBVR (2026)]] — provides large-scale benchmarks to measure world reasoning capabilities and their scaling behavior; read after V-JEPA to understand how physics and reasoning emerge systematically
   - **Alternative entry**: If interested in benchmarking and evaluation rather than learning mechanisms, start here
