---
name: research-start
description: Entry point and router for the research funnel. Use when the user says "start research", "where am I in my research", "what should I do next on my paper", "research status", "/research-start", or starts a new research project. Sets up the project workspace, shows the funnel, finds the current stage, and names the single next action.
---

# Research Start (Router)

Route the user to the right funnel stage and keep one source of truth per project.

## The funnel

| # | Stage | Skill | Gate (human decides) |
|---|---|---|---|
| 1 | Idea | idea-forge | Pick 1 idea to pursue |
| 2 | Gap check | gap-check | Go / pivot / kill |
| 3 | Reading | read-loop | (continuous, no gate) |
| 4 | Study design | study-design | Approve question, data, baselines, metrics |
| 5 | Experiments | experiment-log | Results good enough to write? |
| 6 | Venue | venue-pick | Choose target venue |
| 7 | Drafting | draft-paper | Approve each section |
| 8 | Pre-submit | pre-submit | Submit / fix first |
| 9 | Revision | reviewer-response | Approve rebuttal and changes |

Read `${CLAUDE_PLUGIN_ROOT}/references/gates.md` (gate rules), `workspace.md` (file layout) and `skill-map.md` (which validated skill each stage calls). Stages invoke those skills with the Skill tool rather than redoing their work.

At first run, check which mapped skills are installed. List any missing in one line and suggest the Research Desk plugin; continue with fallbacks.

## Steps

1. Look for a `research/` folder in the working folder. If none exists, create it with the layout in `workspace.md`, including `ideas.md`, `reading-log.md`, and `projects/`.
2. Ask which project (or create `projects/<slug>/status.md` from the template in `workspace.md`).
3. Read `status.md`. Determine the current stage from the last passed gate.
4. Report in at most 6 lines: project, current stage, last gate passed, blockers, deadline, and ONE next action with the skill to run.
5. If a deadline is within 14 days and the stage is before 8, flag it as at risk.
6. Do not run the next stage automatically. Wait for the user.

## Rules

- One next action only. No menus of ten options.
- Update `status.md` whenever a gate is passed (date, decision, reason).
- If the user tries to skip a gate, name what is missing and ask them to confirm the skip in writing; log the skip in `status.md`.
