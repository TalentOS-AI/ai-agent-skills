---
name: semantic-scholar
description: >-
  Use when searching published journal/conference papers via Semantic Scholar
  with citation counts and venue metadata, or looking up a paper by DOI while
  doing a literature review.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# Semantic Scholar Search

Use when searching published venue papers (journals/conferences) with citation counts, venue metadata, and TLDR.

## Setup (portable)

- Public API: `https://api.semanticscholar.org/graph/v1` (docs: https://api.semanticscholar.org/).
- Optional: `SEMANTIC_SCHOLAR_API_KEY` (free key form on Semantic Scholar) — send as header `x-api-key` if 429 without a key.
- Fallback: Crossref + OpenAlex DOI lookup. Do not invent metadata.

## Workflow

1. Parse query or DOI / S2 paper id / `ARXIV:` id.
2. Search (for **management / OB / MBA** topics use broad fields — Business, Psychology, Economics — or omit CS-only filters):
```bash
# Relevance search
curl -sG "https://api.semanticscholar.org/graph/v1/paper/search" \
  --data-urlencode "query=QUERY" \
  --data-urlencode "limit=10" \
  --data-urlencode "year=2015-" \
  --data-urlencode "fields=paperId,title,year,venue,externalIds,citationCount,abstract,tldr,authors" \
  ${SEMANTIC_SCHOLAR_API_KEY:+-H "x-api-key: $SEMANTIC_SCHOLAR_API_KEY"}

# Single paper by DOI / S2 id / ARXIV:…
curl -sG "https://api.semanticscholar.org/graph/v1/paper/DOI:10.xxxx/...." \
  --data-urlencode "fields=paperId,title,year,venue,externalIds,citationCount,abstract,tldr,authors" \
  ${SEMANTIC_SCHOLAR_API_KEY:+-H "x-api-key: $SEMANTIC_SCHOLAR_API_KEY"}
```
3. Show title, venue, year, citationCount, DOI, TLDR/abstract snippet.
4. On 429: backoff/retry with the API key; else Crossref + OpenAlex DOI lookup.
5. Feed verified hits into `review_matrix.csv` (theme, design_implication, verified).

## Provenance

Adapted from [wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep) `skills/semantic-scholar/` (MIT, Copyright 2026 wanshuiyin). Public export uses direct Semantic Scholar HTTP instead of a box-local helper.
