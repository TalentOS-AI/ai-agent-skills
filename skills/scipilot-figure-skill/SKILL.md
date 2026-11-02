---
name: scipilot-figure-skill
description: >-
  Use as a visualization advisor before or while revising scientific data
  figures: chart-type choice, anti-pattern interception (dual Y, pie, rainbow,
  truncated axes, mean bars with tiny n), and visual self-check checklists.
  Complements acl-paper-figures; does not replace ACL print-size style.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# SciPilot figure advisor (local; from Haojae/scipilot-figure-skill, MIT)

Source: https://github.com/Haojae/scipilot-figure-skill
Commit: `43098ddb9e6a6d142218540c114f9ed38922fc42` (2026-10-19 install).
License: MIT — keep `LICENSE-scipilot.txt`. Upstream skill last push 2026-06-15.

**Vetting (2026-10-19):** Local matplotlib/seaborn/plotly tooling; optional
SciencePlots/pypdf/kaleido degrade gracefully. No required API keys. Scripts do
not exfiltrate. **Does not** draw schematics/flowcharts/teasers — those stay on
TikZ / `acl-paper-figures` canvas figures. No ACL column constants — keep
`acl_figstyle.py`.

## When to use / when NOT
- **Use:** picking chart type; auditing for viz pitfalls; visual review checklist
  after render; advising against dual axes / pie / rainbow / bad truncation.
- **NOT:** installing Auto `paper-figure` defaults (`tab10`, `bbox_inches=tight`);
  replacing Okabe-Ito + ACL widths; generating architecture diagrams.

## Anti-pattern checklist (from `references/viz_pitfalls.md`)
Fail if present without justification: mean bars with n<10/group and no raw points;
dual Y-axis for unrelated vars; pie/3D pie; Y truncated to exaggerate bar diffs;
rainbow/jet; connecting categorical means with lines; one figure with >1 core claim;
colour-only encoding without marker/hatch/label; legend colliding with data;
text <6 pt at final size; JPEG for line art; silent `bbox_inches=tight` changing
print size.

## Visual review (from `references/visual_review.md`)
After PNG render: missing glyphs / clipped text / overlapping ticks; legend over
data; panel-label alignment; greyscale separability; consistent scales across
panels; caption-ready uncertainty naming.

Upstream full text: `UPSTREAM-SKILL.md`. See `references/` and `scripts/`.
