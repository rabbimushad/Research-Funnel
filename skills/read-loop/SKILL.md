---
name: read-loop
description: Daily reading habit for researchers. Finds the next paper worth reading for the active project and turns a read paper into a 5-line summary in the reading log. Use when the user says "what should I read next", "summarise this paper in 5 lines", "log this paper", "my reading log", or "reading streak". Funnel stage 3, runs continuously.
---

# Read Loop (Stage 3)

Read at the plugin root: `workspace.md`, `skill-map.md`.

## Mode A — "What should I read next?"

1. Read the active `status.md` and the last 10 entries of `research/reading-log.md`.
2. Invoke **paper-search** for 3 candidates: one foundational (highly cited), one recent (≤18 months), one closest competitor. Skip anything already logged.
3. One line each on why it matters. Recommend one.

## Mode B — "Log this paper"

1. **Attempt first.** Ask the user for their own 5 lines (minimum: the key result in one line).
2. Invoke **research-litnote** on the paper. For a key paper the user wants to understand deeply, invoke **read-paper** instead.
3. Condense its output into the 5-line entry (Problem, Method, Key result with number + page, Limitation, Use for me).
4. Compare with the user's lines: max 3 bullets on what they missed or misread.
5. Append to `research/reading-log.md`. If an idea appears, offer to add it via idea-forge.

## Mode C — "Compare these papers"

Invoke **paper-compare** on 2–5 papers; save the table to the project folder; note which one is the baseline candidate.

## Mode D — "Reading streak"

Count entries per week for 4 weeks; report vs target (default 3/week) in one line.
