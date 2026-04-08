---
topic: sports-analytics
tags: [concept, method, classical-ml, dimensionality-reduction, classification]
---

## Definition

**Linear Discriminant Analysis (LDA)** is a supervised dimensionality reduction and classification technique that finds a linear projection of the feature space maximising the ratio of between-class scatter to within-class scatter. Unlike PCA (which maximises variance regardless of class labels), LDA explicitly optimises for class separability.

## How it works

Given $c$ classes, LDA computes two scatter matrices:

**Within-Class Scatter (SW):** $S_W = \sum_{i=1}^{c} \sum_{x \in C_i} (x - \mu_i)(x - \mu_i)^T$

**Between-Class Scatter (SB):** $S_B = \sum_{i=1}^{c} N_i (\mu_i - \mu)(\mu_i - \mu)^T$

The optimal projection $W$ maximises $\frac{|W^T S_B W|}{|W^T S_W W|}$, solved via generalised eigendecomposition of $S_W^{-1} S_B$.

At inference, a new sample is projected into the LDA subspace and assigned to the nearest class centroid (or via posterior probability under Gaussian assumption).

## Properties relevant to sports analytics

- **Low latency**: projection and nearest-centroid lookup are O(d·k) at inference — suitable for real-time embedded systems
- **Interpretable**: the projection weights reveal which features most discriminate between movement classes
- **Small data friendly**: performs well with hundreds of samples; deep models need orders of magnitude more
- **Limitation**: assumes linear separability and Gaussian class distributions — may underperform on highly non-linear or temporally complex movement patterns

## Papers using this concept

- [[papers/2025-realtime-volleyball-movement-classification-lda|Real-Time Volleyball Movement Classification (Koteda et al., 2025)]] — LDA on 6-axis IMU features for 6-class volleyball action recognition; 99.09% accuracy on 462-sample dataset
- [[papers/2019-volleyball-action-modelling-imu-feedback|Volleyball Action Modelling (Salim et al., 2019)]] — LDA evaluated among 5 classifiers for binary action/non-action detection; not the best performer (NB leads on imbalanced training, accelerometer ~80% UAR LDA vs. ~84% NB)
