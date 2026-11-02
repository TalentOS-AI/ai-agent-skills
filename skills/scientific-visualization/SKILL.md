---
name: scientific-visualization
description: >-
  Use after drafting ACL/EACL/ARR paper figures (with acl-paper-figures) for
  post-figure QA: WCAG contrast and grayscale palette audit, file metadata
  (PDF fonts/DPI), journal export planning, and honesty checklists. Do not
  replace acl-paper-figures for ACL column widths or Okabe-Ito encoding.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# Scientific visualization QA (local; from K-Dense `scientific-visualization`, MIT)

Source: https://github.com/K-Dense-AI/scientific-agent-skills/tree/main/skills/scientific-visualization
Commit: `a1043ef544e3a100c28e70a736b6cf32554d0677` (repo tip at install, 2026-10-19).
License: MIT — keep `LICENSE-K-Dense.md` with any copy. Cite if used in a manuscript:
Kassis et al. (2026), arXiv:2609.00065.

**Vetting (2026-10-19):** Bundled CLIs are network-free; no unexplained secrets.
Plotly/Kaleido Chrome path is optional and unused for our ACL matplotlib PDFs.
Does **not** ship ACL `COLUMN`/`TEXT` constants — keep using `acl-paper-figures`
`assets/acl_figstyle.py`. Rejects silent `bbox_inches="tight"` unless intentional.

## When to use / when NOT
- **Use:** after figures exist; colour/contrast audit; greyscale separation; PDF
  metadata/fonts; publisher checklist planning; integrity / deceptive-encoding review.
- **NOT:** first-pass ACL figure build (use `acl-paper-figures`); Gemini/architecture
  image generation; claiming automated pass = journal acceptance.

## QA playbook (T1 / ACL)
1. Palette: `python scripts/palette_audit.py --palette okabe_ito_on_white --background FFFFFF --role graphical` (and `--role normal-text` for labels).
2. File metadata: `python scripts/image_metadata.py FIG.pdf` (and PNG); check Type 42 fonts, physical size vs ACL column/text width.
3. Export plan (advisory only): `python scripts/export_plan.py --publisher acl` if profile exists, else treat ACL via `acl-paper-figures` widths (3.03 in / 6.30 in).
4. Manual checklist from `references/publication_guidelines.md` + Final review checklist in `UPSTREAM-SKILL.md`: zero baseline for bars, named uncertainty, redundant colour, no dual axes, no decorative 3D, missing values explicit.
5. View greyscale `_grey.png` and colour PNG at print size; do not certify accessibility from CLI alone.

Upstream full text: `UPSTREAM-SKILL.md`. Assets/scripts/references mirrored beside this file.
