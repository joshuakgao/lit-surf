---
title: "Zero-shot World Models Are Developmentally Efficient Learners"
authors: Aw, Kotar, Lee, Kim, Jedoui, Venkatesh, Chen, Frank, Yamins
year: 2026
venue: arXiv
topic: world-models
source: "[[../../raw/world-models/2026/2026-babyzwm-zero-shot-world-models.pdf]]"
thumbnail: "[[../../raw/world-models/2026/thumbnails/2026-babyzwm-zero-shot-world-models.png]]"
tags: [world-models, developmental-learning, zero-shot, causal-inference, intuitive-physics]
---

![](/raw/world-models/2026/thumbnails/2026-babyzwm-zero-shot-world-models.png)

## Summary

This paper introduces the Zero-shot Visual World Model (ZWM), a self-supervised neural network that learns powerful visual-cognitive abilities from minimal, uncurated data—specifically, egocentric video from a single child across development (868 hours from ages 5 months to 5 years, via the BabyView dataset). The key insight is that data-efficient, zero-shot visual cognition emerges from three design principles: (1) a sparse temporally-factored predictor that decouples appearance from dynamics, (2) approximate causal inference to extract visual-cognitive structures without task-specific supervision, and (3) compositional inference to build increasingly complex reasoning abilities. BabyZWM demonstrates competitive performance with supervised state-of-the-art models on depth estimation, motion segmentation, object segmentation, and intuitive physics tasks despite zero task-specific training. Remarkably, the model's developmental trajectory mirrors human child development, and its internal representations align with neural responses in the visual cortex, suggesting the framework captures fundamental principles of how infants acquire physical understanding.

## Key contributions

- **Zero-shot world model architecture**: A sparse temporally-factored masked predictor trained via self-supervised learning that enables zero-shot transfer to diverse visual-cognitive tasks via approximate causal inference (compare predictions under ground truth vs. counterfactual inputs)
- **Data-efficient learning from child experience**: Demonstrates that 868 hours of egocentric video (roughly 3 months of waking experience) suffices to build competent models of depth, motion, segmentation, and physics—far below the scale of typical supervised or self-supervised models
- **Developmental alignment**: Model checkpoints show developmental trajectories paralleling human infant learning progression across visual-cognitive tasks; internal representations correlate with brain activity patterns
- **Compositional inference**: Framework enables composing simple zero-shot extractors into complex reasoning pipelines (e.g., predicting object motion then computing optical flow for segmentation)
- **Bridge between cognitive science and AI**: Provides a computational account for how infants achieve data-efficient, flexible visual cognition without massive labeled datasets

## Method

**Core learning mechanism**: A sparse temporally-factored masked multi-frame visual predictor Ψ trained on video frame pairs. Given frame f₁ and a sparsely masked frame f₂ (f₂_masked), the model predicts the full frame f₂. Training minimizes L₂ reconstruction loss on ground-truth frame pairs, operating in pixel space with no task labels.

**Zero-shot extraction via causal inference**: After training, the model extracts task-specific visual-cognitive structures (depth, segmentation, optical flow) through approximate causal inference: comparing predictions conditioned on ground-truth inputs (e.g., true depth map revealed) versus counterfactual inputs (depth withheld). The difference in predictions serves as a zero-shot readout for that visual factor.

**Compositional inference**: Complex tasks are solved by chaining simple extractors. For example, segmenting moving objects: (1) predict how an object's appearance changes given hypothetical motion, (2) compute the resulting optical flow differences, (3) use flow magnitude to identify moving regions.

**Training data**: BabyView dataset—egocentric video recordings from children ages ~5 months to 5 years; 868 hours total with varying visual environments and developmental curricula.

## Results

- **Competitive zero-shot performance**: On depth estimation (NYU Depth v2), motion segmentation (DAVIS), object segmentation (COCO), and violation-of-expectation physics probes, BabyZWM achieves performance comparable to supervised baselines and prior self-supervised models, despite zero task-specific training or labeled examples
- **Developmental trajectory alignment**: Evaluating checkpoints from early to late training reveals learning progressions that qualitatively match documented milestones in infant visual-cognitive development (e.g., motion perception, object permanence)
- **Brain alignment**: Model internal representations (learned features and predictions) correlate with fMRI/neural responses in the human visual cortex, suggesting the learned structure captures biologically plausible principles
- **Generalization across visual diets**: Model trained on varied real-world egocentric data generalizes robustly to standard benchmarks despite distribution shift from natural infant video to curated datasets

## Relation to prior work

Extends the trajectory from supervised deep learning → self-supervised representation learning → flexible zero-shot visual cognition. Related to [[2025-intuitive-physics-self-supervised-pretraining|V-JEPA's discovery of intuitive physics from masked video modeling]], but BabyZWM goes further by (1) operating on naturalistic child video rather than curated data, (2) achieving zero-shot multitask transfer via causal inference, and (3) directly grounding the model in developmental and neuroscientific principles. Complements [[2026-vbvr-very-big-video-reasoning|VBVR's large-scale video reasoning benchmark]] by providing a specific architectural approach to achieving flexible visual reasoning with minimal data.

## Open questions / limitations

- **Causality and intervention**: While the paper uses approximate causal inference (comparing predictions), it remains unclear how well this scales to true causal reasoning or counterfactual interventions beyond the visual domain
- **Scalability beyond single-child data**: All experiments use single-child recordings; unclear how performance changes with multi-child or diverse population data
- **Task coverage**: Evaluated on a specific set of visual-cognitive tasks (depth, motion, segmentation, physics); generalization to other domains (semantic understanding, abstract reasoning) not yet explored
- **Comparison to other developmental approaches**: Limited comparison to other computationally grounded developmental models or alternative inductive biases

