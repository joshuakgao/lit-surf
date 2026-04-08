# Denoising Segmentations — Index

Annotation noise—including class label errors, boundary distortions, and weak annotations from foundation models—poses a critical challenge to real-world segmentation pipelines. This wiki tracks literature on understanding, characterizing, and mitigating the effects of noisy annotations on instance and semantic segmentation models, with particular emphasis on robust training methods and benchmarks for evaluation.

## Papers by year

### 2025
- [[papers/2025-noisy-annotations-segmentation|Noisy Annotations in Semantic Segmentation]] — Systematically characterizes annotation noise patterns and introduces COCO-N, CityScapes-N, VIPER-N benchmarks for robustness evaluation
<img src="/wiki/denoising-segmentations/papers/2025-noisy-annotations-segmentation.png" height="300"/>

### 2023
- [[papers/2023-denoising-diffusion-semantic-segmentation|Denoising Diffusion Semantic Segmentation with Mask Prior Modeling]] — Uses discrete diffusion to learn mask priors and refine segmentation predictions, achieving +3 mIoU improvements on ADE20K
<img src="/wiki/denoising-segmentations/papers/2023-denoising-diffusion-semantic-segmentation.png" height="300"/>

## Concepts
- [[concepts/label-noise|Label Noise]] — Incorrect or inaccurate annotations in training data
- [[concepts/instance-segmentation|Instance Segmentation]] — Task of identifying and delineating individual object instances
- [[concepts/learning-from-noisy-labels|Learning from Noisy Labels]] — Techniques for training robust models despite imperfect annotations
- [[concepts/diffusion-models|Diffusion Models]] — Generative models that learn to reverse iterative data corruption through denoising

## See also
- [[../anomaly-detection/index|Anomaly Detection]] — Related robustness challenges in out-of-distribution detection
- [[../video-understanding/index|Video Understanding]] — Spatial-temporal noise in video annotations
