---
topic: world-models
---

# World Models — Overview

*Last updated: 2026-04-16 | Sources: 3 papers*

## Current thesis

World models are learnable and measurable at scale through self-supervised prediction, and moreover, can be acquired from minimal naturalistic data with developmental plausibility. V-JEPA (2025) shows that intuitive physics emerges from representation-space prediction without explicit supervision. VBVR (2026) benchmarks world reasoning at scale across five cognitive capabilities. BabyZWM (2026) demonstrates that data-efficient zero-shot visual-cognitive abilities emerge from just 868 hours of egocentric child video (3 months of waking experience) using sparse temporally-factored prediction and approximate causal inference. Together, these papers establish: (1) representation-space prediction is a sufficient inductive bias for physics understanding, (2) diverse reasoning capabilities generalize systematically when benchmarked at scale, and (3) architectural choices (factorization, causal inference) enable learning from human-scale data while matching developmental trajectories and neural alignment with infant brains.

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
- **Data-efficient learning from naturalistic child video**: BabyZWM learns diverse visual-cognitive abilities (depth, motion, segmentation, intuitive physics) from just 868 hours of egocentric video. Challenges assumption that world models require massive datasets; opens path toward human-scale data efficiency.
- **Zero-shot extraction via approximate causal inference**: BabyZWM introduces a general interface for extracting task-specific predictions from a single trained predictor by comparing counterfactual inputs. Shifts from task-specific readout training to universal zero-shot prompting.
- **Developmental alignment and neural plausibility**: BabyZWM exhibits learning trajectories paralleling human infant development and internal representations correlating with fMRI responses. Provides evidence that architectural choices (sparse temporal factorization) capture cognitively and biologically plausible learning principles.

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

**Data efficiency and scaling (BabyZWM):**
- **Scaling to larger datasets**: BabyZWM trains on 868 hours (single child); how does performance scale with multi-child data or larger datasets? Is there a plateau or continued improvement?
- **Generalization beyond child video**: BabyZWM trained on egocentric child video; robustness to other egocentric domains (robotics, adult POV, synthetic) unexplored
- **Complex real-world physics**: Evaluation focuses on simple object dynamics; soft bodies, friction, fluids, complex interactions not tested
- **True causal reasoning**: Approximate causal inference compares predictions; whether model supports true counterfactual interventions ("what if I push that?") is unclear
- **Scaling to richer semantics**: Model learns appearance/dynamics factorization; integration with semantic understanding (object categories, agent intentions) is open

**Integration:**
- **Physics ↔ Task reasoning**: Can V-JEPA's physics improve VBVR task performance? Do task-trained models develop emergent physics?
- **Joint evaluation**: No existing benchmark that simultaneously measures physics understanding and task reasoning
- **BabyZWM ↔ VBVR**: Does BabyZWM's data-efficient learning scale to VBVR's 200 tasks? Can zero-shot extraction rival VBVR's rule-based evaluation?
- **Data-efficient architectures for benchmarking**: Can BabyZWM's architectural principles (sparse factorization, causal inference) improve sample efficiency on VBVR?

## Contradictions and debates

- **Core knowledge vs. learned emergence**: Traditional developmental psychology argues physics is innate ("core knowledge"). V-JEPA's success suggests learned emergence, but may reflect specific inductive biases of the architecture rather than true "learning from scratch."

## Recommended reading order

1. [[papers/2025-intuitive-physics-self-supervised-pretraining|V-JEPA Intuitive Physics (2025)]] — establishes that representation-space prediction learns physics without explicit supervision; entry point for understanding emergent world models from self-supervised learning
2. [[papers/2026-babyzwm-zero-shot-world-models|BabyZWM (2026)]] — demonstrates data-efficient learning and zero-shot transfer from naturalistic child video; shows how architectural choices enable both developmental plausibility and flexible inference; bridges self-supervised learning with cognitive science
3. [[papers/2026-vbvr-very-big-video-reasoning|VBVR (2026)]] — provides large-scale benchmarks to measure world reasoning capabilities and their scaling behavior; read last to see how diverse reasoning tasks measure progress from foundational physics to complex reasoning
   - **Alternative entry (evaluation-focused)**: Start with VBVR if interested in benchmarking rather than learning mechanisms
