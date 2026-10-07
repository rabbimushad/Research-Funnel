---
name: idea-forge
description: Generate and score novel research ideas, then save them to a central idea bank. Use when the user says "give me research ideas", "find a novel angle", "what paper should I write", "brainstorm topics for X", "add this to my idea bank", or "show my ideas". Funnel stage 1.
---

# Idea Forge (Stage 1)

Read at the plugin root (`${CLAUDE_PLUGIN_ROOT}/references/`, or `../../references/`): `gates.md`, `novelty-rubric.md`, `skill-map.md`, `workspace.md`.

## Steps

1. **Attempt first.** Ask the user for 1–3 rough ideas or a one-line interest, plus constraints (field, data access, months available). Wait.
2. **Expand.** For each seed, generate the 3 strongest angles using these levers: new population/region/culture; new modality pairing; method transfer from a neighbouring field; flip a taken-for-granted assumption; real-world constraint (low resource, occlusion, privacy, edge); evaluation gap (fairness, robustness, cross-dataset, longitudinal).
3. **Validate with the validated skill.** Invoke **fasttrack-topic-validator** on the top 3 angles (general research track: Convergence, Duplication, Impact, one-sentence question). Let it run its own searches and worksheets.
4. **Score** each angle with `novelty-rubric.md`, feeding in the validator's duplication evidence. Show the 5-part breakdown.
5. **Save** every angle to `research/ideas.md` (append; next free ID).
6. **GATE 1 — Pick.** Compare with the user's own pick. Recommend one. For a close call between two ideas, invoke **decision-matrix**. On the user's choice: status `chosen`, create `projects/<slug>/status.md`, log the gate.

## "Show my ideas"

List `research/ideas.md` by status then novelty: ID, title, score, status.
