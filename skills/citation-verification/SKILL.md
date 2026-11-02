---
name: citation-verification
description: >-
  Use before sharing any reference list, related-work section or BibTeX file, to
  resolve every citation against an authoritative source and flag the ones that
  cannot be verified.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# Citation verification
Why it matters: venues now desk-reject papers that contain fabricated references (ACL-family policies treat hallucinated citations as grounds for rejection), so every entry must resolve.
1. Pull every reference out into a list: title, authors, year, and DOI/arXiv/Anthology id if known.
2. Resolve each one, in this order:
   - DOI: `curl -sL -H "Accept: application/x-bibtex" https://doi.org/DOI` (returns official BibTeX). Metadata: `curl -s https://api.crossref.org/works/DOI`.
   - ACL Anthology: `https://aclanthology.org/ID.bib` (e.g. 2020.acl-main.1); Anthology DOIs are 10.18653/v1/ID.
   - arXiv: `curl -s --max-time 60 "http://export.arxiv.org/api/query?id_list=ARXIVID"`. If a published version exists, cite that instead.
   - No id: search Crossref `https://api.crossref.org/works?query.bibliographic=TITLE&rows=3` or OpenAlex, and accept only an exact title match (case and punctuation insensitive) with a matching first author and year.
3. Check that the title, all authors, year and venue match. Fix any field that drifted.
4. Label each entry VERIFIED (with its source URL), CORRECTED (list what changed) or UNVERIFIABLE. Remove UNVERIFIABLE entries or ask the author about them. Never invent fields.
5. Build refs.bib only from the fetched BibTeX, with consistent keys. Optional lint: install pybtex in a venv (system pip may be blocked by PEP 668) and run `python3 -c "import pybtex.database as d;d.parse_file('refs.bib')"`.
6. Check that every claim attributed to a paper actually appears in that paper (open the PDF or abstract).
