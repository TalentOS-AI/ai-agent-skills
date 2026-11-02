---
name: openalex
description: >-
  Use when searching academic literature via OpenAlex for citation data, DOI
  metadata, affiliations, or funding—especially while building or verifying a
  review matrix.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# OpenAlex Academic Search

Use when searching academic literature via OpenAlex (citation graph, affiliations, funding, DOI metadata).

## Setup (portable)

- Public API: `https://api.openalex.org` (docs: https://developers.openalex.org/).
- Optional env vars for higher limits / polite pool:
  - `OPENALEX_API_KEY` (free at openalex.org)
  - `OPENALEX_EMAIL` (mailto in User-Agent for polite pool)
- Fallback if OpenAlex returns 429 / budget exhausted: Crossref `https://api.crossref.org/works?query.bibliographic=...`. Do not invent metadata.

## Workflow

1. Parse query + optional filters: max, year (`2023` / `2020-2023`), type, open-access, min-citations, sort.
2. Search works (URL-encode QUERY; add mailto when `OPENALEX_EMAIL` is set):
```bash
# Search
curl -sG "https://api.openalex.org/works" \
  --data-urlencode "search=QUERY" \
  --data-urlencode "per-page=10" \
  --data-urlencode "select=id,doi,title,publication_year,primary_location,cited_by_count,open_access,authorships" \
  ${OPENALEX_EMAIL:+--data-urlencode "mailto=$OPENALEX_EMAIL"} \
  ${OPENALEX_API_KEY:+-H "Authorization: Bearer $OPENALEX_API_KEY"}

# By DOI (also accepts OpenAlex work id W…)
curl -sG "https://api.openalex.org/works/https://doi.org/10.xxxx/...." \
  ${OPENALEX_EMAIL:+--data-urlencode "mailto=$OPENALEX_EMAIL"}
```
3. Present a table: title, venue, year, citations, OA, DOI; note design implication if building a review matrix.
4. For management / OB / MBA topics, do **not** filter to Computer Science only.
5. On 429: switch to Crossref or the `semantic-scholar` skill; do not invent metadata.

## Provenance

Adapted from [wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep) `skills/openalex/` (MIT, Copyright 2026 wanshuiyin). Public export uses direct OpenAlex/Crossref HTTP instead of a box-local helper.
