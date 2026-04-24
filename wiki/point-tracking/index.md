---
topic: point-tracking
---

# Point Tracking — Index

Long-term tracking of points across video frames — from optical flow over sparse correspondence to dense trajectory prediction. Covers synthetic-to-real domain adaptation, multi-tracker ensembling, and robust supervision strategies for real-world videos.

## Papers by year

### 2026
- [[papers/2026-verifier-real-world-point-tracking|Real-World Point Tracking with Verifier-Guided Pseudo-Labeling]] — meta-model learns per-frame reliability of tracker predictions; adaptive pseudo-label selection from multiple trackers; synthetic-trained reliability transfers to real videos
<img src="/raw/point-tracking/2026/thumbnails/2026-verifier-real-world-point-tracking.png" height="300"/>

## Concepts

- [[concepts/point-trajectory|Point Trajectory]] — 2D or 3D trajectory of a point across frames; core output of point tracking
- [[concepts/synthetic-to-real-adaptation|Synthetic-to-Real Adaptation]] — bridging domain gap between synthetic training and real-world videos; handling appearance, motion, and occlusion differences
- [[concepts/ensemble-tracking|Ensemble Tracking]] — combining predictions from multiple trackers to improve robustness

## See also

- [[../video-understanding/index|Video Understanding]] — broader category; point tracking as primitive for temporal reasoning
- [[../3d-scene-reconstruction/index|3D Scene Reconstruction]] — point trajectories used for 4D reconstruction and motion estimation
