---
topic: visual-localization
tags: [concept, task]
---

## Definition

Image retrieval is the task of finding similar images in a database given a query image, typically using global descriptors that summarize the entire image content. In localization, image retrieval provides a coarse search stage that identifies candidate locations before fine-grained geometric matching.

## Origins

Image retrieval has been studied for decades in content-based image search. Early work used hand-crafted descriptors (bag-of-words, VLAD). Modern approaches leverage CNN features for more robust global representations.

## Key variants / extensions

- **Global descriptors**: Single vector summarizing entire image (e.g., from CNN features or pooling)
- **Bag-of-words models**: Quantizing local features into discrete visual words
- **VLAD (Vector of Locally Aggregated Descriptors)**: Aggregating local features spatially
- **Metric learning**: Training descriptors to maximize similarity of related images
- **Efficient search**: Using approximate nearest neighbors (hashing, product quantization) for scalability

## Papers using this concept

- [[2019-hierarchical-localization-at-large-scale]] — Uses global CNN descriptors for efficient coarse retrieval in hierarchical localization pipeline
