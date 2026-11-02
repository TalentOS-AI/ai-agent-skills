---
name: acl-paper-figures
description: >-
  Use when making or fixing data figures or a Figure-1 teaser for an ACL-style
  (ACL/EMNLP/NAACL/EACL/ARR/workshop) or other two-column paper: print-size
  matplotlib figures from result files, colour-blind and greyscale safe, with an
  automatic audit and a self-critique loop.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# ACL paper figures (local; adapted from alphaXiv/OpenResearch `orx-figures`, MIT)

Source: https://github.com/alphaXiv/OpenResearch/tree/main/agent-skills/orx-figures (commit 6285fee7, vetted 2026-10-19). Vetting: pure matplotlib and numpy, no network, no keys. `assets/acl_figstyle.py` is the upstream `orx_figstyle.py` with ACL widths, a serif default, PNG and greyscale previews and a CJK-as-outline helper. License notice: `assets/LICENSE-orx-figures.txt` (keep it with any copy).
Rejected alternatives: Orchestra `academic-plotting` (its diagram workflow sends prompts to Gemini and needs `GEMINI_API_KEY`; its plotting template uses `bbox_inches="tight"`, which changes the printed size). Norman-bury `figures-python` (conda- and macOS-font-specific; PNG and SVG at 450 dpi rather than vector PDF at final size).

## Steps
1. **Message first.** For each figure write the caption's bold first sentence, the claim, before writing any code. If two panels do not support one claim, make them two figures.
2. **Study the genre once per project.** Look at 8–12 strong papers in the venue: Figure 1 teaser, how they show a model × condition gap, captions. Usual patterns: minimal-pair teaser with real model outcomes; paired dots per model, sorted by the key metric; spread across nuisance variants shown alongside the mean. Write the lessons to `figures/figure-design-notes.md`.
3. **Set up.** Use a venv with `pip install matplotlib numpy pandas`. Copy `assets/acl_figstyle.py` next to the figure scripts (e.g. `paper/scripts/figures/`) together with the LICENSE file.
4. **Data.** Read every number from the analysis output (JSON or CSV that the tables also use). Never type numbers by hand. Put caption numbers in a generated macros file (`\providecommand`). Parse model display names from the table script so names cannot drift. Make missing or invalid arms drop out automatically, keyed on a validity flag in the data.
5. **Build at print size.** ACL (A4, 2.5 cm margins): `COLUMN = 3.03 in`, `TEXT = 6.30 in`. Check with `\the\columnwidth` (219.09 pt) and `\the\textwidth` (455.24 pt). Use `use_style()` (Times-metric serif, Type 42 fonts). Axis labels 9 pt, ticks 8 pt, annotations at least 7 pt. No axes titles; the caption is the title.
6. **Encodings.** Position on a common scale (dots, bars from zero; Cleveland & McGill). Categories go on the y axis as horizontal text. Keep the same row order in every figure. Okabe-Ito colours carry one meaning paper-wide, and references are grey. Redundant encoding (side, fill, shape) keeps the figure readable in greyscale. Label directly; use a legend only inside empty space. Show CIs, and show per-variant points (seeds, prompt wordings) when they disagree.
7. **Teaser.** Draw on a full-figure inch canvas (`xlim=(0, W)`, `ylim=(0, H)`): the input shared by the pair, the one changed span highlighted, the gold labels, then 2–4 systems' outcomes as bars computed from the data. Use `cjk_text()` for CJK snippets so no CFF font gets embedded.
8. **Save and audit.** `save(fig, stem)` writes PDF, PNG and `_grey.png`, and prints an audit (width, fonts, sizes below 6 pt, overlapping or clipped text). The audit must say `clean`.
9. **Self-critique, at least two rounds.** Open each PNG (copy it to a new filename first if the viewer caches), critique it like a reviewer against the notes (message visible without the text? overlaps? contrast? greyscale? misleading axes?), fix, and repeat. Record what changed in the notes.
10. **Test in LaTeX.** Make a scratch doc with the venue `.sty`, `\includegraphics[width=\columnwidth]` or `[width=\textwidth]` in `figure`/`figure*`, and the macros. Compile it, check `pdffonts` (no Type 3), and view the page at print scale. Do not edit the paper's main `.tex` if someone else owns it; hand over a `snippet.tex` instead.

## Caption pattern
`\textbf{Claim in one sentence.}` Then what each mark, colour and interval means (with n and CI type), what is truncated or excluded, and one number that makes the claim concrete (as a macro).
