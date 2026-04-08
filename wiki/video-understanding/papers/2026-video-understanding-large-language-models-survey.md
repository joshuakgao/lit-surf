---
title: "Video Understanding With Large Language Models: A Survey"
authors: Tang, Yunlong; Bi, Jing; Xu, Siting; Song, Luchuan; Liang, Susan; Wang, Teng; Zhang, Daoan; An, Jie; Lin, Jingyang; Zhu, Rongyi; Vosoughi, Ali; Huang, Chao; Zhang, Zeliang; Liu, Pinxin; Feng, Mingqian; Zheng, Feng; Zhang, Jianguo; Luo, Ping; Luo, Jiebo; Xu, Chenliang
year: 2026
venue: IEEE Transactions on Circuits and Systems for Video Technology (TCSVT)
topic: video-understanding
source: "[[raw/video-understanding/2026/2026-video-understanding-large-language-models-survey.pdf]]"
thumbnail: "[[raw/video-understanding/2026/thumbnails/2026-video-understanding-large-language-models-survey.png]]"
tags:
  - survey
  - vid-llm
  - video-qa
  - video-captioning
  - taxonomy
  - multimodal
  - reasoning
  - temporal-grounding
---

![](/raw/video-understanding/2026/thumbnails/2026-video-understanding-large-language-models-survey.png)

## Summary

A comprehensive survey of video understanding with large language models (Vid-LLMs), documenting the landscape through June 2024. The paper provides a structured taxonomy of how LLMs are integrated into video understanding pipelines, covering 3 main architectural paradigms and 5 functional roles. This survey fills a gap left by prior works that either focus on specific sub-tasks (video captioning, action recognition) or general video foundation models without centering on LLM-based approaches.

Key finding: LLMs have shifted video understanding from specialized task-specific models to general-purpose reasoners capable of open-ended multi-granularity reasoning (abstract, temporal, spatiotemporal). The emergent capability is handling questions that require combining visual understanding with common-sense knowledge and external context.

## Taxonomy of Vid-LLMs

The paper structures the landscape through:
- **3 architectural paradigms**: Analyzer×LLM, Embedder×LLM, hybrid
- **5 functional roles**: Summarizer, Manager, Text Decoder, Regressor, Hidden Layer

## Evolution of video understanding methods

The paper frames four evolutionary stages:
1. **Conventional Methods** (pre-2010): handcrafted features (SIFT, HOG), HMM, SVM, optical flow
2. **Early Neural Models** (2010–2019): CNN, two-stream networks, 3D CNN (C3D, I3D), LSTM, vision transformers
3. **Self-Supervised Pretraining** (2018–2023): VideoBERT, VideoMAE, CLIP-ViP, pretraining-finetuning paradigm shift
4. **Large Language Models** (2023–2024): in-context learning, instruction-tuning, LLMs as task-agnostic solvers for video

## Vid-LLM taxonomy

### Three architectural paradigms

**1. Video Analyzer × LLM:**
- Video analyzer converts video to *textual descriptions* (captions, scene graphs, detected objects)
- LLM processes text only; task becomes NLP
- Advantage: training-free (no video encoder parameters need updating)
- Disadvantage: information loss in text conversion
- Examples: Visual-ChatGPT, SlowFast-LLaVA

**2. Video Embedder × LLM:**
- Video embedder encodes video into *vector embeddings* (frozen or fine-tuned)
- LLM processes embeddings; visual information preserved
- Advantage: richer signal than text; emergent multimodal reasoning
- Disadvantage: requires fine-tuning; higher computational cost
- Examples: VideoChat2, VideoLLaMA 2, MiniGPT4-Video

**3. (Analyzer + Embedder) × LLM:** (rare)
- Hybrid: LLM receives both textual analysis AND embeddings
- Combines benefits of both approaches
- Examples: VideoChat, Vid2Seq, Vamos

### Five LLM functional roles

**LLM as Summarizer:**
- Generates summaries from video or region-of-interest descriptions
- Output: structured summaries
- Examples: VideoChat, MiniGPT4-Video

**LLM as Manager:**
- Orchestrates calls to other models/APIs (vision models, external tools)
- Output: predictions via tool invocations
- Examples: Visual-ChatGPT, GroundingGPT (early works)

**LLM as Text Decoder:**
- Receives text inputs and generates text outputs
- Primary use case: video QA, captioning, grounding descriptions
- Examples: InternVideo2, VideoLLaMA 2, Video-LLaVA

**LLM as Regressor:**
- Predicts continuous values (timestamps, bounding box coordinates)
- Output: regression predictions + text
- Examples: VTimeLLM, SeViLA, TimeChat, LITA

**LLM as Hidden Layer:**
- LLM not directly outputting text; instead embedded as feature transformation
- Task-specific heads attached to LLM for final predictions
- Output: structured predictions (timestamps, boxes) via task head
- Examples: VITRON, VTGLLM, Momentor

## Training strategies

### Training-free Vid-LLMs
- No parameter updates; rely on LLM's zero-shot, in-context learning, chain-of-thought
- Most Video Analyzer × LLM systems
- Example: SlowFast-LLaVA

### Fine-tuning Vid-LLMs
Four adapter-based approaches (Figure 6 in paper):

1. **LLM Fully Fine-tuning**: update all LLM parameters; resource-intensive; risks losing zero-shot capability; better performance on target task
2. **Connective Adapter Fine-tuning**: freeze LLM, train only modality-alignment adapter (MLP, Q-former); preserves zero-shot; efficient; most common
3. **Insertive Adapter Fine-tuning**: freeze LLM, train LoRA-based adapters inserted into LLM; affects LLM behavior; enables regression/grounding tasks
4. **Hybrid Adapters**: two-stage or joint training of Connective + Insertive; achieves both alignment and task-specific behavior

## Video understanding tasks covered

### Abstract-level (requires classification/generation, no temporal reasoning)
- Video classification & action recognition
- Text-video retrieval
- Video-to-text summarization
- Video captioning
- Video QA (multiple-choice and open-ended)

### Temporal-level (requires reasoning about when)
- Video summarization
- Highlight detection
- Temporal action localization
- Dense video captioning
- Video temporal grounding
- Moment retrieval
- Event boundary detection

### Spatiotemporal-level (requires reasoning about where AND when)
- Object tracking
- Re-identification
- Video-based grounding (boxes + timestamps)
- Spatiotemporal action localization

## Benchmarks and evaluation

### Closed-ended evaluation
- Multiple-choice questions: TVQA, TGIF-QA, MSRVTT-QA, ActivityNet-QA
- Metric: Top-K accuracy
- Advantage: straightforward scoring; standardized

### Open-ended evaluation
- Free-form questions: MovieChat-1K, MLVU, NExT-QA, VELOCITI, EAGLE
- Metric: GPT-3.5/4 evaluation (compare model output to reference)
- Advantage: more human-aligned; tests deeper reasoning
- Limitation: evaluation unstable across GPT versions; prompt-dependent; may favor LLM-like outputs

### Temporal/spatiotemporal evaluation
- Temporal grounding: tIoU (temporal Intersection-over-Union), Recall@K
- Dense captioning: BLEU, METEOR, CIDEr, ROUGE-L
- Tracking: precision, success rate

### Key performance drivers (from Tables III & IV)
1. **Foundation model size**: larger LLMs (e.g., 34B) outperform smaller ones in zero-shot
2. **Visual encoder quality**: EVA-CLIP, ViT-G consistently better than weaker encoders
3. **Frame sampling strategy**: temporal models process 100+ frames vs. 8–10 for general models
4. **Adapter sophistication**: Q-formers, cross-attention > simple projection layers

## Key trends & findings

- **Unified reasoning paradigm**: all tasks (QA, captioning, grounding, summarization) can be framed as generation/regression; LLMs solve them as variants
- **Temporal reasoning bottleneck**: models with explicit temporal modeling (VTimeLLM, ST-LLM) needed for temporal/grounding tasks; generic visual encoders insufficient
- **In-context learning capability**: Vid-LLMs can adapt to new tasks with few examples; zero-shot performance competitive with task-specific models
- **Modality gap**: precise alignment between visual embeddings and LLM token space is critical; Q-former/cross-attention adapters outperform simple projections
- **Emergence of meta-reasoning**: advanced models combine LLM reasoning with tool-use (calling vision models, APIs) for complex tasks

## Applications

- **Media & Entertainment**: search, recommendation, subtitle generation, video editing, scene generation
- **Autonomous Driving**: object detection, scene understanding, driving behavior analysis
- **Surveillance & Security**: action recognition, anomaly detection, event localization
- **Robotics**: instruction following, object interaction understanding
- **Medical Video Analysis**: procedure recognition, abnormality detection
- **Education**: lecture understanding, knowledge extraction, automatic captioning

## Open challenges & future directions

1. **Long-form video understanding**: current models cap at ~768 frames; hierarchical coarse-to-fine temporal search remains unsolved
2. **Temporal grounding precision**: high QA accuracy does not guarantee precise temporal localization (noted in [[papers/2025-moma-qa-fine-grained-video-question-answering|MOMA-QA]])
3. **Evaluation metric instability**: GPT-based evaluation scores fluctuate with LLM version; need more robust metrics
4. **Domain shift**: models train on web videos; performance on specialized domains (medical, scientific) unclear
5. **Computational cost**: many Vid-LLMs require significant GPU resources; efficient, lightweight models needed for deployment
6. **Multi-event reasoning**: questions spanning entire video length remain challenging
7. **Causal reasoning**: distinguishing causal from correlational relationships in video remains weak
8. **Audio-visual understanding**: most survey focuses on visual; audio integration is underdeveloped

## Relation to other video understanding papers in wiki

- [[papers/2025-moma-qa-fine-grained-video-question-answering|MOMA-QA (2025)]] and [[papers/2025-timesearch-r-temporal-search-video-understanding|TimeSearch-R (2025)]]: both are instantiations of Vid-LLM paradigm; this survey is the meta-framework
- MOMA-QA is Video Embedder (scene graph) + LLM, functioning as Regressor for temporal grounding
- TimeSearch-R is Video Embedder + RL-trained LLM for adaptive search; uses LLM as Manager of search operations
