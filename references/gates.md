# Human-in-the-loop gates

The funnel is fast because Claude does the mechanical work. It stays honest because a human makes every decision that shapes the research.

## Gate rules

1. **Attempt first.** Before Claude produces its answer at a gate, ask the user for their own attempt (one line is enough): their pick, their guess at the weakness, their research question. Then compare. This trains judgment; skipping it trains dependence.
2. **Claude recommends, the human decides.** End every stage with a GATE block:

   ```
   GATE <n> — <name>
   Recommendation: <one line>
   Evidence: <2–3 bullets>
   Risks: <1–2 bullets>
   Your decision: go / change / stop
   ```
   Then stop and wait.
3. **Never invent evidence.** Citations, datasets, numbers and results must come from a tool result, a file, or the user. Mark anything unverified `[UNVERIFIED]`.
4. **Log the decision** in `projects/<slug>/status.md` gate log: date, stage, decision, reason.
5. **Kill is a valid outcome.** A killed idea goes back to `ideas.md` with status `killed` and the reason. That is progress, not failure.

## What only the human does

- Chooses the problem and the claimed contribution.
- Runs and debugs experiments; owns the data.
- Writes the contribution paragraph and the main claim of the abstract.
- Fixes the top issues from review (Claude may suggest, the human edits).
- Clicks submit.

## What Claude does without asking

- Searching, retrieving, deduplicating papers.
- Formatting, reference lookup, checklists, tables, logs.
- First drafts of mechanical sections (related work from supplied sources, dataset description, reference list).
