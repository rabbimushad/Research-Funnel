---
name: gap-check
description: Stress-test one chosen research idea before investing months: duplication search, literature map, closest prior work, feasibility, and a go/pivot/kill call. Use when the user says "has this been done", "is my idea novel", "check the gap", "validate my topic", or after an idea is chosen in idea-forge. Funnel stage 2.
---

# Gap Check (Stage 2)

Read at the plugin root: `gates.md`, `novelty-rubric.md`, `skill-map.md`.

## Steps

1. **Attempt first.** Ask the user to write the research question in one line: *"Can [method] [improve/explain] [outcome] for [population/setting] compared with [baseline]?"* Correct it together.
2. **Duplication test.** Invoke **fasttrack-topic-validator** on the question (if not already run in stage 1, or if the question changed).
3. **Closest work.** Invoke **paper-search** with 4–6 phrasings (method alone, population alone, dataset name, outcome), and also query Consensus/SciSpace/PubMed connectors if present. Build a closest-work table (max 8): citation, year, what they did, how this idea differs. Tool-returned papers only.
4. **Literature map (optional, recommended for journal papers).** Invoke **literature-review-helper** for a full search plan and synthesis document; save its output into `projects/<slug>/`.
5. **Feasibility.** Data (public? license? size), compute, skills, time to first result. Ask the user.
6. **Rescore** with the novelty rubric using real evidence.
7. **GATE 2 — Go / Pivot / Kill.** Compare with the user's own call. For a kill or a major pivot, invoke **llm-council** for a second opinion first. Pivot = 2 concrete re-angles. Kill = update `ideas.md` with reason. Log in `status.md`.

## Rules

- If a paper already does the exact idea, say so in the first line.
- Thin search results = "low coverage", never "no prior work".
