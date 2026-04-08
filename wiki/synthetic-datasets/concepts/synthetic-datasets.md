---
topic: synthetic-datasets
tags: [concept, method]
---

## Definition

Synthetic datasets are collections of computer-generated images with automatically generated ground truth labels and annotations. They address the challenge that obtaining dense per-pixel labels from real images is expensive, time-consuming, or sometimes impossible. Synthetic datasets can be photorealistic (aiming to match real image appearance) or stylized (prioritizing ease of generation/annotation).

## Origins

Early synthetic datasets (Pascal3D+, ShapeNet) used simple 3D models. Recent photorealistic datasets (Hypersim, Replica, OpenRooms) leverage professional 3D assets and physically-based rendering for improved realism and downstream sim-to-real transfer.

## Key variants / extensions

- **Photorealistic**: Aiming to closely match real image appearance (Hypersim, Replica)
- **Stylized**: Simplified rendering prioritizing annotation efficiency (SceneNet-RGBD)
- **Public assets**: Using only publicly available 3D models (Hypersim)
- **Proprietary assets**: Using non-public professional models (InteriorNet)
- **Real-based**: Derived from real-world 3D reconstructions (ScanNet, Matterport3D)
- **Artist-created**: Hand-crafted by professional artists (Hypersim, Replica)

## Papers using this concept

- [[2021-hypersim-photorealistic-synthetic-dataset-indoor-scene]] — Introduces comprehensive photorealistic synthetic dataset with public assets, complete annotations, and strong sim-to-real transfer
