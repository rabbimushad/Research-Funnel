---
name: experiment-log
description: Keep a clean, reproducible log of experiment runs and turn it into results tables and figures. Use when the user says "log this run", "add results", "make the results table", "compare my runs", "plot my results", or "are my results good enough to write". Funnel stage 5.
---

# Experiment Log (Stage 5)

Gate rules: `references/gates.md` at the plugin root (`${CLAUDE_PLUGIN_ROOT}/references/`, or `../../references/`).

## Log a run

Append to `projects/<slug>/experiments.md` one row per run:

| Run ID | Date | Config / change | Data split | Seed | Metric(s) | Notes |

Ask for any missing field. Numbers come only from the user or their files (logs, CSVs); never estimate.

## Results table

1. Group runs by method; compute mean ± std over seeds by running code, not by hand.
2. Produce a results table comparing the method with every baseline in `design.md`, and an ablation table.
3. If a chart helps, build it from the logged numbers.

## GATE 5 — Ready to write?

Check against `design.md`:
- Every hypothesis tested?
- All planned baselines and ablations run?
- Statistics done (seeds or significance)?
- Any result that contradicts the claim, explained?

Recommend: write now / run X more / rethink claim. Ask the user to decide; log it in `status.md`.

## Rules

- Report negative and null results honestly; they shape the claim.
- Warn on signs of leakage (test score far above validation, near-perfect accuracy on hard tasks).
