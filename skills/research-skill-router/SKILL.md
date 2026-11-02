---
name: research-skill-router
description: >-
  Use at the start of any academic research task (literature search, citation
  check, stats, figures, paper writing, venue templates, mock review, rebuttal)
  to pick the right existing skill and install an external one on demand.
version: 1.2.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# Research skill router (install on demand)

Rule: prefer a local skill first; only fetch an external skill when the task actually needs it. Never pre-install.

## 1. Route by task
| Task | Local skill (use first) | External candidates (MIT unless noted) |
|---|---|---|
| Literature search / systematic review | literature-review, openalex, semantic-scholar | K-Dense-AI/scientific-agent-skills: literature-review; wanshuiyin/Auto-claude-code-research-in-sleep: openalex, semantic-scholar; Norman-bury/research-writing-skill: literature-review; alphaXiv/OpenResearch: orx-lit-review; wp-a/nature-academic-search; Yuan1z0825/nature-skills: nature-academic-search (Apache-2.0); fcakyon/labrat: literature-research (renamed from phd-skills); mikubaka88/CCFA-Skills: ccf-literature-searcher, ccf-literature-monitor (Chinese-friendly) |
| ACL Anthology lookup | literature-review | antins-labs/SearchOS: searchos/skills/library/access/aclanthology-org (fetch record + BibTeX by Anthology ID only, no keyword search; needs aiohttp, bs4) |
| Novelty check | literature-review | Auto-claude-code-research-in-sleep: novelty-check; microsoft/ResearchStudio: ResearchStudio-Idea/skills/scoop_check (prior-art delta statement) |
| Citation verification / BibTeX | citation-verification, citation-audit | Auto-claude-code-research-in-sleep: citation-audit; K-Dense: citation-management, pyzotero; AlterLab-IEU/AlterLab-Academic-Skills: alterlab-citation-verifier; wp-a/nature-academic-search; Yuan1z0825/nature-skills: nature-ref-verifier (Apache-2.0); ShaishavMaisuria/research-paper-lifecycle-skills: verify-citations (Apache-2.0; Crossref/DBLP/S2/arXiv + retraction); mikubaka88/CCFA-Skills: ccf-integrity-auditor (claims, numbers, citations) |
| Venue choice / deadlines / templates | venue-deadlines, acl-latex-paper | K-Dense: venue-templates; brycewang-stanford/Awesome-Journal-Skills (ACL / EACL / EMNLP / NAACL packs; EACL `eacl-submission` for ARR cycle + OpenReview commit); ShaishavMaisuria/research-paper-lifecycle-skills (Apache-2.0): select-venue (CCF/CORE-aware shortlist), parse-cfp (venue profile from live CFP), plan-submission (AoE-aware backwards timeline, OpenReview steps); mikubaka88/CCFA-Skills: ccf-submission-checker (venue package / submission checklist) |
| Dataset & annotation / agreement | annotation-project | Votee-AI/magic-agent-skills: magic-linguistic-annotate (Apache-2.0; IAA κ/α/γ + guidelines); AlterLab-IEU/AlterLab-Academic-Skills: alterlab-qualitative-analysis (Krippendorff α / Cohen·Fleiss κ); pjt222/agent-almanac: label-training-data |
| Statistics / power analysis | - | K-Dense: statistical-analysis, statistical-power; Norman-bury/research-writing-skill: statistical-analysis |
| LLM evaluation | - | Orchestra-Research/AI-Research-SKILLs: lm-evaluation-harness, bigcode-evaluation-harness, nemo-evaluator |
| Figures | acl-paper-figures (local, from alphaXiv/OpenResearch orx-figures, MIT; installed 2026-10-19); scientific-visualization (local QA from K-Dense, MIT; 2026-10-19); scipilot-figure-skill (local anti-pattern advisor from Haojae, MIT; 2026-10-19) | Yuan1z0825/nature-skills: nature-figure (Apache-2.0); Orchestra academic-plotting (Gemini key — reference only); Norman-bury figures-python (conda/raster — rejected); Auto paper-figure (MIT but default tab10 + bbox_inches=tight — do not install defaults; skim workflow only) |
| Paper writing | acl-latex-paper, deslop | Orchestra: ml-paper-writing, systems-paper-writing; Master-cai/Research-Paper-Writing-Skills; zLanqing/codex-claude-academic-skills (Chinese-first); mikubaka88/CCFA-Skills: ccf-paper-writer (CCF-A storyline, Chinese-aware), ccf-humanization (anti-defensive preflight); Norman-bury/research-writing-skill: writing-core; stephenturner/skill-deslop; MohamedAbdallah-14/unslop; Adkid-Zephyr/anti-defensive-writing-Skill: anti-defensive-writing (+ EN twin anti-defensive-writing-en; press-release principle); Yuan1z0825/nature-skills: nature-writing, nature-polishing (Apache-2.0); alphaXiv/OpenResearch: orx-paper; fcakyon/labrat: paper-write (absorbs old paper-writing + latex-setup) |
| LaTeX to arXiv | acl-latex-paper | appautomaton/latex-arxiv-SKILL; Auto-claude-code-research-in-sleep: paper-compile; Norman-bury/research-writing-skill: latex-output; fcakyon/labrat: paper-write (LaTeX setup path via references/latex.md) |
| Mock review before submission | - | Spark-To-Paper-Skills/paperjury; K-Dense: peer-review; Orchestra: rigor-reviewer; AlterLab: alterlab-peer-review, alterlab-paper-reviewer; Norman-bury: peer-review; mikubaka88/CCFA-Skills: ccf-paper-reviewer; Yuan1z0825/nature-skills: nature-reviewer (Apache-2.0); claesbackman/AI-research-feedback: review-paper (8-agent referee report; economics/finance journals JF/JFE/RFS) |
| Rebuttal / response letter | rebuttal-letter | Auto-claude-code-research-in-sleep: rebuttal; Awesome-Journal-Skills author-response (ACL/EACL/EMNLP/NAACL); fcakyon/labrat: rebuttal (was reviewer-defense); mikubaka88/CCFA-Skills: ccf-rebuttal-writer (Chinese-aware); Yuan1z0825/nature-skills: nature-response (Apache-2.0) |
| Reference only (no/unclear license; read, never copy text) | - | Imbad0202/academic-research-skills (NOASSERTION / CC-BY-NC-4.0), lingzhi227/agent-research-skills, TobiasLee/Rebuttal-Skill, HKUSTDial/Supervisor-Skills, AIScientists-Dev/academic-humanizer, brycewang-stanford/Auto-Empirical-Research-Skills, tizzy916/humanities-writing-companion, HughYau/AcademicForge (NOASSERTION hub) |

Gaps still open (as of 2026-11-02): ACL Anthology keyword search (only fetch-by-ID via SearchOS); dedicated ARR calendar (partial: Awesome-Journal `eacl-submission`, research-paper-lifecycle `plan-submission`); FinNLP / financial-text NLP (no open-license research skill found); Chinese pragmatics / hedging annotation (Votee discourse covers Mandarin zero-anaphora only; anti-defensive skills are prose style, not annotation).

Full inventory (1,665 entries, stars, licenses): keep a local `skills-inventory/` CSV beside your research notes; this public skill does not ship private inventory paths.

## 2. Install on demand
1. Re-check the repo via GitHub API: still exists, license (MIT/Apache OK; none/NOASSERTION means reference only), last push.
2. Fetch only the needed skill folder (`gh api repos/OWNER/REPO/contents/PATH` or sparse `git clone --depth 1 --filter=blob:none --sparse`).
3. Read SKILL.md and any scripts fully. Reject anything that exfiltrates data, needs unexplained secrets, or runs remote code blindly.
4. Check dependencies (API keys, paid services, packages; use a venv if system pip is blocked) and do one small test run.
5. Save it as a local skill (UpdateSkill) with attribution to the source repo and license in the body; keep the license notice.
6. Update the table above to mark it as local.
