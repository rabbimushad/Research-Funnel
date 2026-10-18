---
name: read-loop
description: Fast, targeted reading for researchers. Suggests the next papers with a speed-read map (3-line summary, triage tier, exactly which sections to read and what to look for, time estimate), builds a weekly reading plan, and logs each paper as a 5-line note. Use when the user says "what should I read next", "reading plan", "how should I read this paper", "summarise this paper", "log this paper", "my reading log", or "reading streak". Funnel stage 3, runs continuously.
---

# Read Loop (Stage 3)

Read at the plugin root: `workspace.md`, `skill-map.md`, `speed-read.md` (map format, tiers), `router.md` (which skills are weak).

## Mode A — "What should I read next?"

1. Read the active `status.md` and the last 10 entries of `research/reading-log.md`.
2. Invoke **paper-search** for 3 candidates: one foundational (highly cited), one recent (≤18 months), one closest competitor. Skip anything already logged.
3. For each, produce a **speed-read map** per `speed-read.md`: tier, time, 3-line summary, the 2–4 parts to read with an active-reading question each, what to skip. Use research-litnote or the paper text to ground the pointers.
4. Recommend reading order.

## Mode A2 — "Reading plan"

Propose 5–8 papers for the week in a table (title, tier, minutes, why), within the reading budget (default 90 min/week), then the map for the first one.

## Mode B — "Log this paper"

0. If the user has not read it yet, give the speed-read map first and stop.
1. **Attempt first.** Ask the user for their own "Use for me" line (minimum), or their 5 lines.
2. Invoke **research-litnote** on the paper. For a key paper the user wants to understand deeply, invoke **read-paper** instead.
3. Condense its output into the 5-line entry (Problem, Method, Key result with number + page, Limitation, Use for me).
4. Compare with the user's lines: max 3 bullets on what they missed or misread.
5. Append to `research/reading-log.md`. If an idea appears, offer to add it via idea-forge.

## Mode C — "Compare these papers"

Invoke **paper-compare** on 2–5 papers; save the table to the project folder; note which one is the baseline candidate.

## Mode D — "Reading streak"

Count entries per week for 4 weeks; report vs target (default 3/week) in one line.
