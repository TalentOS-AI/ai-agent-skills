---
name: citation-audit
description: >-
  Use before sharing any reference list, related-work section, or proposal
  bibliography to verify every entry is real, correctly attributed, and supports
  the claim; complements citation-verification.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# Citation audit (MBA-friendly)

Use before sharing any reference list, related-work section, or proposal bibliography: verify every entry is real, correctly attributed, and supports the claim. Complements the `citation-verification` skill.

## Zero-context rule

Do not trust titles/authors/years from memory or from an unverified draft. Resolve each item.

## Resolve order

1. DOI → `curl -sL -H "Accept: application/x-bibtex" https://doi.org/DOI` and Crossref `https://api.crossref.org/works/DOI`
2. No DOI → Crossref `query.bibliographic=TITLE` — accept only exact title + matching first author + year
3. Optional enrichment: OpenAlex (`https://api.openalex.org/works/...`) or Semantic Scholar (`https://api.semanticscholar.org/graph/v1/paper/...`); see `openalex` and `semantic-scholar` skills. Optional env: `OPENALEX_API_KEY`, `OPENALEX_EMAIL`, `SEMANTIC_SCHOLAR_API_KEY`.
4. Label: **VERIFIED** (with source URL) / **CORRECTED** (list changes) / **UNVERIFIABLE** (remove or ask user)

## MBA / Chinese journal notes

- Chinese CSSCI items may lack Crossref DOI: keep title/author/year/journal; mark UNVERIFIABLE or PENDING until CNKI/official page confirmed; never invent volume/pages.
- Working papers (e.g. NBER): cite working-paper status honestly if not yet journal-published.
- Every claim that cites a number (e.g. g=−0.23, +14%) must appear in that paper — open PDF/abstract to check.

## Output

Update `review_matrix.csv` `verified` column; write a short verification report with counts and CORRECTED/UNVERIFIABLE lists.

## Provenance

Adapted from [wanshuiyin/Auto-claude-code-research-in-sleep](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep) `skills/citation-audit/` (MIT, Copyright 2026 wanshuiyin); shortened for agent + management/MBA workflow. Public export uses DOI/Crossref/OpenAlex/S2 HTTP only (no box-local helpers).
