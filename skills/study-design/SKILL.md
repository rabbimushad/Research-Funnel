---
name: study-design
description: Turn a validated research question into a concrete study plan: hypotheses, datasets, baselines, metrics, ablations, statistics, threats to validity, and timeline. Use when the user says "design my study", "plan my experiments", "which baselines should I use", "what metrics", or after a Go at gap-check. Funnel stage 4.
---

# Study Design (Stage 4)

Read at the plugin root: `gates.md`, `skill-map.md`.

## Steps

1. **Attempt first.** Ask for the planned dataset, main baseline, and main metric (one line each).
2. **Baseline choice.** Invoke **paper-compare** on the 2–5 strongest papers from the closest-work table to pick the baseline(s) and metrics the field expects.
3. Write `projects/<slug>/design.md`:
   - Question and 1–3 falsifiable hypotheses (with the result that rejects each)
   - Contribution claim — one sentence the user writes or approves
   - Data: source, license, size, splits, preprocessing, ethics/consent
   - Baselines (cited) + one simple baseline
   - Metrics: primary, secondary, and why
   - Ablations for each component
   - Statistics: seeds/folds, CIs or significance test
   - Threats to validity: leakage, bias, cross-dataset generalisation
   - Weekly timeline to first and full results
4. **Design review.** Invoke **paper-critique** on `design.md` as if it were a methods section; take its top 3 issues.
5. **GATE 4 — Approve design.** Log in `status.md`.
