---
name: research-autopilot
description: Run the research funnel automatically from idea to submission-ready paper, with Claude doing the work and the human giving input only at five hard checkpoints (idea go, run access, results spot-check, main claim, submit). Use when the user says "autopilot", "run my research automatically", "do the research yourself", "fully automated research", "continue autopilot", or "run the funnel end to end".
---

# Research Autopilot

Read at the plugin root (`${CLAUDE_PLUGIN_ROOT}/references/`, or `../../references/`) before starting: `autopilot.md` (checkpoints, inbox, integrity), `skill-map.md` (which validated skill each stage calls), `workspace.md` (files), `novelty-rubric.md`.

## Mode switch

In autopilot, the funnel stage skills behave as follows:
- **Attempt-first is skipped.** Do not ask the human for their own attempt.
- **Soft gates become `[AUTO]` decisions.** Decide, log the reason, continue.
- **Hard checkpoints H1–H5 always stop.** See `autopilot.md`.
- Questions go to `inbox.md` with a default taken, never as a blocking chat question.

## Start or resume

1. Find or create `research/`. Read the active project's `status.md`, `inbox.md`, and `provenance.md` (create from templates if missing).
2. Apply any newly answered inbox items; re-run only the work they affect.
3. Determine the current stage from the gate log and continue from there.
4. If no project exists: take the user's topic or the highest-novelty `new`/`testing` idea in `research/ideas.md`; if neither exists, ask once for a field and constraints, then proceed.

## Pipeline

Run each stage by following its funnel skill in autopilot mode, invoking the validated skills named in `skill-map.md`:

| Stage | Funnel skill | Autopilot output | Stops at |
|---|---|---|---|
| 1 Idea | idea-forge | 3–5 scored angles in `ideas.md`; best one selected `[AUTO]` | — |
| 2 Gap check | gap-check | closest-work table, rescored novelty, go/pivot/kill recommendation | **H1 Go** |
| 3 Reading | read-loop | 15–30 core papers logged as 5-line entries | — |
| 4 Design | study-design | `design.md`, critiqued and revised once | **H2 Run access** (if keys, data access, ethics or budget are needed) |
| 5 Experiments | experiment-log | runnable code in `projects/<slug>/code/`, run log, results tables, figures | **H3 Spot-check** |
| 6 Venue | venue-pick | `venue.md` with first choice + fallback `[AUTO]` | — |
| 7 Draft | draft-paper | full draft in venue format; contribution and abstract claim proposed | **H4 Main claim** |
| 8 Pre-submit | pre-submit | critique → fix → re-critique loop (max 2 rounds), citation check, numbers check, disclosure, comprehension brief | **H5 Submit** |
| 9 Revision | reviewer-response | revision plan + response letter when reviews arrive | human approves letter |

## Experiments (stage 5) specifics

- Write code that the human can rerun: pinned dependencies, seeds, config file, one command to run, outputs saved as CSV.
- Run what can be run in this workspace (public data, local models, analysis). For anything needing the human's credentials, paid APIs, or their machine, write a `RUN_ME.md` with exact steps and expected output size/cost, mark H2 as `BLOCKING`, and stop after finishing all independent work.
- After results arrive, run all statistics by code and generate the H3 spot-check sample (random, stratified across conditions) as a file for the human to review.

## Self-review loop (stage 8)

1. Invoke **paper-critique**; fix every major issue Claude can fix without new data; log fixes in `provenance.md`.
2. Invoke **citation-check**; replace or remove every unverified reference.
3. Re-run paper-critique once. Anything still major that needs new experiments or the human's judgment goes to `inbox.md`.
4. Generate the AI-use disclosure and the comprehension brief (see `autopilot.md`).

## End of every run

Write the run report from `autopilot.md` (max 10 lines) in chat and append it to `status.md`. Name exactly what the human must provide, or "nothing — say 'continue autopilot'".

## Rules

- Never fabricate citations, data, or results. If a step cannot be done honestly, stop that branch and record why.
- Never submit, email editors, or create accounts on the human's behalf.
- Long runs: work stage by stage, saving files after each, so a run can be resumed at any point.
