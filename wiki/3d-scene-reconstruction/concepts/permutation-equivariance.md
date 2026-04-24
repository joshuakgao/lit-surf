---
topic: 3d-scene-reconstruction
tags: [concept, property]
---

## Definition

Permutation equivariance is an architectural property where a model's predictions are invariant to the ordering of its inputs. For visual geometry, it means that if you provide the same set of images in different orders, the model produces the same outputs (up to a consistent coordinate frame). Technically: a permutation-equivariant function $f$ satisfies $f(\sigma(x)) = \sigma(f(x))$ for any permutation $\sigma$ of the input, where the permutation acts symmetrically on both input and output.

## Origins

Permutation equivariance emerged from research on set functions and symmetric neural networks (Zaheer et al., Kondor & Trivedi). Applied to point clouds and unordered sets, it ensures that models respect the fundamental property of sets—elements have no inherent ordering. The concept has been extensively explored in graph neural networks and set-based architectures but is relatively new to visual geometry reconstruction.

## Key variants / extensions

- **Permutation invariance**: Weaker property; outputs are invariant to input ordering but can be unordered themselves (e.g., set of poses without correspondence to specific images). Permutation equivariance is stronger—maintains the correspondence.
- **Partial permutation equivariance**: Equivariant only to meaningful permutations (e.g., temporal order is semantically significant in videos, so full equivariance may be unnecessary or undesirable)
- **Coupled with scale/translation invariance**: π³ combines permutation equivariance with affine-invariant poses and scale-invariant depth, creating a fully symmetric representation

## Papers using this concept

- [[../papers/2026-pi3-permutation-equivariant-visual-geometry-learning|π³: Permutation-Equivariant Visual Geometry Learning]] — introduces permutation equivariance to 3D reconstruction; demonstrates that fully equivariant architecture eliminates reference-view selection bias and improves robustness
