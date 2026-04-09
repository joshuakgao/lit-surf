---
topic: world-models
tags: [concept, method]
---

## Definition

Violation of Expectation (VoE) is an experimental paradigm from developmental psychology that measures infants' surprise when observed events contradict expected physical laws. Empirically, infants look longer at implausible events (e.g., object disappearing without exiting the frame), indicating they maintain expectations about how the world should behave.

## Origins

Pioneered by Renée Baillargeon and colleagues (Baillargeon, 1986; Baillargeon et al., 1992) to probe infants' intuitive physics understanding. Demonstrates that human infants understand object permanence, solidity, and continuity without explicit instruction. Extended to primates, corvids, and other species.

## Key variants / extensions

- **Infant testing**: Measure looking time / gaze patterns
- **Animal testing**: Track physiological surprise indicators or approach/avoidance behavior
- **AI probing**: Measure model prediction error ("surprise") to detect physics violations; enables zero-shot evaluation without task-specific training (Riochet et al., 2022; Piloto et al., 2022)
- **Datasets**: IntPhys (synthetic object trajectories), GRASP (contact physics), InfLevel (liquid physics)

## Papers using this concept

- [[2025-intuitive-physics-self-supervised-pretraining|Intuitive Physics (V-JEPA)]] — adapts VoE to AI by measuring representation-space prediction error; videos with physics violations produce higher surprise (mismatch between predicted and observed future)
