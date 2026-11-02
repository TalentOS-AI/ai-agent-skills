---
name: annotation-project
description: >-
  Use when building a labeled dataset (annotation scheme, guidelines, LLM
  pre-annotation, human adjudication, inter-annotator agreement, data statement
  and licensing).
version: 1.0.0
owner: Iris
dept: 科研
status: active
public: true
updated: 2026-11-02
---
# Dataset / annotation project
1. Sourcing: check the site's terms of service, robots.txt and the copyright/license of the data. Record provenance (URL and crawl date) for every item. Strip personal data you don't need.
2. Scheme: define labels grounded in the literature, each with a definition, positive and negative examples, and decision rules for borderline cases. Write guidelines.md and version it.
3. Pilot: have 2+ annotators label 50-100 items, compute agreement, revise the guidelines, and repeat until agreement is stable.
4. LLM pre-annotation (optional): use a fixed prompt, model, version and temperature 0, and log everything. Humans must review every item. Report LLM-human agreement separately, and keep an untouched human-only subset so you can measure LLM bias.
5. Agreement (if system pip is blocked by PEP 668: `python3 -m venv ~/.venv-research && ~/.venv-research/bin/pip install scikit-learn statsmodels krippendorff`):
   - 2 annotators: `sklearn.metrics.cohen_kappa_score(a,b)`. Use `weights='quadratic'` for ordinal labels.
   - Fixed group of 3+ annotators: `statsmodels.stats.inter_rater.fleiss_kappa(aggregate_raters(M)[0])`.
   - Missing labels or any setup: `krippendorff.alpha(reliability_data=R, level_of_measurement='nominal')` (rows = annotators, use np.nan for missing).
   Report agreement per label plus a confusion matrix, and resolve disagreements through a documented adjudicator.
6. Splits: train/dev/test with no leakage (split by entity or time). Publish baselines.
7. Release: write a data statement (Bender & Friedman 2018) or datasheet, pick a license (e.g. CC BY-NC 4.0 if the source requires it), and publish the guidelines, annotator pay and demographics if collected, and the intended uses. Go through ethics review if human subjects are involved.
