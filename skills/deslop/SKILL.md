---
name: deslop
description: >-
  Use when reviewing or revising academic prose (esp. Chinese journal drafts) to
  remove AI writing tells: stacked connectives, antithetical boilerplate,
  defensive hedging, formulaic structures, filler transitions.
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# Deslop (academic)

Adapted from [stephenturner/skill-deslop](https://github.com/stephenturner/skill-deslop) (MIT). Strip predictable AI patterns from manuscripts.

## Quick checks (run before delivering)
- Cut filler: 「值得注意的是」「综上所述」「在此基础上」「不难发现」; EN: it's worth noting, despite these challenges, in conclusion, navigate the landscape, delve.
- Break formulaic binary contrasts (Not X. Y.), tricolon stacks, rhetorical Q→immediate A.
- Prefer direct claims; put caveats once in limitations—no repeated preemptive apologetics.
- Active voice with clear actors (we / 本文 / named systems).
- Vary sentence rhythm; avoid metronomic parallel couplets (对仗套话).
- No meta-announcements of what the section will do unless the venue template requires it.
- Score 1–10 on Directness / Rhythm / Trust / Authenticity / Density; below 35/50 → revise.

## Chinese journal extras (科技管理研究-style)
- Prefer 问题→做法→发现→启示 over ACL-style contribution laundry lists.
- Cut stacked connectives (此外/同时/进一步/因此 连用).
- Scope claims: example/probe language when scenario is illustrative.

## Output
List flagged spans with location + rewrite; apply fixes only when the user asked to edit, or when the parent task is a full self-check-and-fix.

## Provenance
Upstream: https://github.com/stephenturner/skill-deslop (MIT). Local adaptation adds Chinese journal boilerplate checks.
