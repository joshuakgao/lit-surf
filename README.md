# LitSurf

> This is my implementation of Andrej Karpathy's LLM Wiki that he tweeted about. 

I have created a custom CLAUDE.md that may be useful to you as it supports thumbnail photos for each paper, and identifies trends over time for a research topic.

## Usage

```claude
ingest bridge-eqa.pdf # add bridge-eqa.pdf to reading-list
ingest https://arxiv.org/pdf/2412.07612

lint # to clean up, reorganize, and avoid contradictions in wiki's

# Ask Claude to traverse your Wiki's and answer questions
What are some research gaps in the world-models literature?
```