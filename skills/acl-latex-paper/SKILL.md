---
name: acl-latex-paper
description: >-
  Use when writing or compiling a paper for an ACL-style venue
  (ACL/EMNLP/NAACL/EACL/ARR/workshops) in LaTeX, including anonymization,
  required sections and a compile check.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# ACL-style LaTeX paper
1. Template: `git clone --depth 1 https://github.com/acl-org/acl-style-files` (or the venue's Overleaf template). Do not change margins or fonts. Use `\usepackage[review]{acl}` for submission and `[final]` for camera-ready.
2. Structure: Abstract, Intro (state contributions), Related Work, Method/Data, Experiments, Results/Analysis, Conclusion, then **Limitations** (required, unnumbered, does not count toward pages), Ethics Statement (if relevant), References, Appendix. Fill in the ARR Responsible NLP checklist.
3. Page limits: long papers 8 pages, short papers 4 (check the CFP).
4. Anonymize: no names or affiliations, refer to your own work in the third person, use anonymized repo links (anonymous.4open.science), remove PDF metadata and acknowledgments.
5. Compile:
   - Install once: `curl --proto '=https' -fsSL https://drop-sh.fullyjustified.net | sh && sudo mv tectonic /usr/local/bin/` (or `apt-get install latexmk texlive-latex-extra texlive-fonts-recommended`).
   - Build: `tectonic -X compile main.tex` or `latexmk -pdf main.tex`.
   - Check: `pdfinfo main.pdf` (page count, no author metadata), `grep -i "undefined" main.log`, and no "??" in the PDF (`pdftotext main.pdf - | grep -n '??'`).
6. Before submitting: run the citation-verification skill, confirm every figure is readable in grayscale, and check every number in the text against the tables.
