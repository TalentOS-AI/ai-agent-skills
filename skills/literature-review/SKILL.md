---
name: literature-review
description: >-
  Use when you need a systematic literature search or review on a research topic
  (finding papers, snowballing, building a review matrix) before choosing a
  topic or writing related work.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# Literature search & systematic review
1. Write the protocol first: research question, inclusion/exclusion criteria, years, venues (e.g. ACL/EMNLP/NAACL + field journals), 3-6 query strings. Save as protocol.md.
2. Query several sources (they cover different things). Log each query, date and hit count:
   - OpenAlex (journals + conferences): `curl -s "https://api.openalex.org/works?search=QUERY&per-page=50&select=id,doi,title,publication_year,primary_location,cited_by_count"` (add `&mailto=you@x`; no key means a small shared daily budget).
   - Semantic Scholar: `curl -s "https://api.semanticscholar.org/graph/v1/paper/search?query=QUERY&limit=50&fields=title,year,venue,externalIds,citationCount"`. Often returns 429 without a key; wait and retry with backoff.
   - arXiv preprints: `curl -s --max-time 60 "http://export.arxiv.org/api/query?search_query=all:QUERY&max_results=50"` (Atom XML; can be slow, use a timeout and retry).
   - ACL Anthology: search https://aclanthology.org or `pip install acl-anthology` (in a venv) for offline metadata.
   - Crossref for journals: `curl -s "https://api.crossref.org/works?query=QUERY&rows=50"`.
3. Remove duplicates by DOI, then arXiv id, then normalized title. Screen titles and abstracts against the criteria, and record the reason for every exclusion.
4. Snowball 1-2 rounds on the core papers: backward via `.../paper/{id}/references`, forward via `.../paper/{id}/citations` (Semantic Scholar) or OpenAlex `filter=cites:W...`.
5. Build review_matrix.csv with columns: id,doi,title,year,venue,task,data,method,metrics,key_result,limitations,relevance(1-3),verified. Read the full text for every relevance-3 paper.
6. Synthesize: group papers by theme, write a gap table (what exists / what is missing / evidence), and report PRISMA-style counts (found, screened, included).
7. Run the citation-verification skill on every paper you cite. Never cite a paper from memory.
