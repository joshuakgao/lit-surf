# Lit Surf — Schema

A personal literature review wiki for AI research and related fields. The LLM maintains the wiki; the human curates sources and asks questions.

---

## Directory structure

```
reading-list/          # Drop unread papers/articles here (PDFs or MDs)
raw/                   # Ingested source documents (immutable after filing)
  {topic-slug}/        # e.g., "diffusion-models", "mechanistic-interpretability"
    {year}/            # e.g., "2024"
      paper-name.pdf
      paper-name.md    # Optional markdown companion or clipped article
wiki/                  # LLM-maintained literature review wikis
  {topic-slug}/
    index.md           # Topic index: all papers listed by year, with one-line summaries
    overview.md        # Running synthesis: key trends, open problems, evolving thesis
    concepts/          # Key concepts, methods, architectures, terms
      concept-name.md
    papers/            # Individual paper summaries
      YYYY-short-title.md
index.md               # Master index: all topics with links and descriptions
log.md                 # Append-only chronological log of all operations
CLAUDE.md              # This file
```

---

## Topic slugs

Use lowercase kebab-case. Examples:
- `diffusion-models`
- `mechanistic-interpretability`
- `in-context-learning`
- `rlhf`
- `world-models`

When ingesting a paper, determine the most appropriate topic slug. If it straddles multiple topics, pick the primary one. If the topic doesn't exist yet, create it.

---

## Ingest workflow

Triggered when the user says "ingest [filename]" or similar.

1. **Read** the document from `reading-list/` — for `.pdf` files, use `pdftotext file.pdf -` via Bash to extract text
2. **Discuss** key takeaways with the user — ask if there's a particular angle or emphasis they want
3. **Request thumbnail** — ask the user to paste in an image to use as the paper thumbnail (appears in summaries and index)
4. **Determine** topic slug, publication year, and a canonical filename (from paper metadata or content)
5. **Rename and move** the file: `reading-list/filename` → `raw/{topic-slug}/{year}/YYYY-short-title.ext`
   - Canonical filename format: `YYYY-kebab-case-title.ext` (e.g., `2024-attention-is-all-you-need.pdf`)
   - Derive the title from the actual paper/article title, not the original filename
   - Keep it concise: drop articles (a, an, the) and filler words if the title is long; preserve key nouns
6. **Save thumbnail** — save the image as `wiki/{topic-slug}/papers/YYYY-short-title.png` (or .jpg)
7. **Create** paper summary: `wiki/{topic-slug}/papers/YYYY-short-title.md`
8. **Update** topic index: `wiki/{topic-slug}/index.md` — add the paper to the correct year section with one-line summary and thumbnail
9. **Update** concept pages: create or update `wiki/{topic-slug}/concepts/` pages for key methods, terms, and ideas introduced or used by the paper
10. **Update** overview: `wiki/{topic-slug}/overview.md` — integrate new findings, note agreements/contradictions with existing literature, update trend observations
11. **Update** master index: `index.md` — add the topic if new, or confirm it's already listed
12. **Append** to `log.md`: `## [YYYY-MM-DD] ingest | {Topic} | {Paper Title}`

A single ingest typically touches 5–15 files. Do all updates in one pass.

---

## Page formats

### Paper summary (`wiki/{topic}/papers/YYYY-short-title.md`)

```markdown
---
title: "Full Paper Title"
authors: Last, Last, Last
year: YYYY
venue: NeurIPS / ICML / arXiv / etc.
topic: topic-slug
source: "[[raw/{topic}/{year}/filename.pdf]]"
thumbnail: "[[raw/{topic}/{year}/thumbnails/YYYY-short-title.png]]"
tags: [tag1, tag2]
---

![](/raw/{topic}/{year}/thumbnails/YYYY-short-title.png]])

## Summary

2–4 paragraph summary of the paper's contribution, method, and findings.

## Key contributions

- Bullet list of the 3–5 most important contributions

## Method

Brief description of the approach. Include architecture details, training setup, or key equations if important.

## Results

What they showed and on what benchmarks/datasets.

## Relation to prior work

How this paper builds on, contradicts, or advances other work in this wiki.

## Open questions / limitations

What the paper leaves unresolved or where the approach may not generalize.
```

IMPORTANT: the `source` property must be formatted as `"[[raw/{topic}/{year}/filename.pdf]]"`, and the `thumbnail` property must be formatted as `"[[raw/{topic}/{year}/thumbnails/YYY-short-title.png]]"`.
### Concept page (`wiki/{topic}/concepts/concept-name.md`)

```markdown
---
topic: topic-slug
tags: [concept, method/architecture/term]
---

## Definition

What this concept is.

## Origins

Where it came from, what paper introduced it.

## Key variants / extensions

Notable variations developed in subsequent work.

## Papers using this concept

- [[YYYY-paper-title]] — one-line note on how/why
```

### Topic index (`wiki/{topic}/index.md`)

```markdown
# {Topic Name} — Index

{One-paragraph description of the topic and scope of this wiki}

## Papers by year

### YYYY
- [[papers/YYYY-short-title|Full Title]] — one-line summary
<img src="/raw/{topic}/{year}/thumbnails/YYYY-short-title.png" height="300"/>

### YYYY
- ...

## Concepts
- [[concepts/concept-name|Concept Name]] — one-line description

## See also
- [[../other-topic/index|Other Topic]] — why it's related
```

IMPORTANT:
- Make sure there is no whitespace before the `<img />` or else the image won't render
- Do NOT include `width` property on images — only use `height="300"` to preserve original aspect ratio
### Topic overview (`wiki/{topic}/overview.md`)

```markdown
# {Topic Name} — Overview

*Last updated: YYYY-MM-DD | Sources: N papers*

## Current thesis

A 2–4 sentence synthesis of what the literature currently shows. Updated with every ingest.

## Key trends

Narrative or bullet list of how the field has evolved year by year.

## Open problems

The unresolved questions the literature keeps circling.

## Contradictions and debates

Areas where papers disagree.

## Recommended reading order

For someone new to this topic: which papers to read first and why.
```

### Master index (`index.md`)

```markdown
# Lit Surf — Master Index

## Topics

| Topic | Pages | Papers | Last updated |
|-------|-------|--------|--------------|
| [[wiki/topic-slug/index\|Topic Name]] | N | N | YYYY-MM-DD |

## Reading list

Files currently in `reading-list/` awaiting ingest.

## Stats

Total papers ingested: N
Topics: N
```

---

## Query workflow

When the user asks a question:

1. Read `index.md` to identify relevant topics and pages
2. Read the topic `index.md` and `overview.md` for those topics
3. Read specific paper summaries and concept pages as needed
4. Synthesize an answer with citations (link to paper summary pages)
5. If the answer is substantive and reusable, offer to file it as a new page in the relevant `wiki/{topic}/` directory

---

## Lint workflow

When the user asks for a lint/health-check:

1. Check for orphan pages (no inbound links)
2. Check for concepts mentioned in summaries but lacking their own page
3. Check `overview.md` for claims that newer papers may have updated
4. Check the topic index for missing year sections or incomplete entries
5. Suggest papers that would fill obvious gaps, based on citations in existing summaries
6. Report findings as a checklist the user can act on
7. Create/remove/reorganize topics and the papers in those topics for better paper organization

---

## Conventions

- All internal links use Obsidian wiki-link format: `[[path/to/file|Display Name]]`
- Source links in paper frontmatter point to raw files: `[[raw/topic/year/file.pdf]]`
- Dates: ISO 8601 (`YYYY-MM-DD`)
- Year directories: four-digit year only (`2024/`, not `2024-papers/`)
- Topic slugs: lowercase kebab-case, no years in the slug
- Paper summary filenames: `YYYY-short-title.md` (year prefix for chronological sorting)
- Log entries: `## [YYYY-MM-DD] {operation} | {Topic} | {Detail}` — one entry per operation
- Never modify files in `raw/` once filed
- Never modify files in `reading-list/` except to move them to `raw/` during ingest
