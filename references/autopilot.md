# Autopilot mode

In autopilot, Claude runs every stage end to end without waiting at each gate. The human is asked only for what Claude cannot or must not decide. Everything else is decided by Claude, logged with a reason, and reversible.

## The 5 hard checkpoints (always stop)

These are never automated, because they need the human's judgment, resources, or legal responsibility.

| # | Checkpoint | Why it cannot be automated |
|---|---|---|
| H1 | **Go on the idea** (after gap-check) | Months of the human's time; the human must want this paper |
| H2 | **Run access** — API keys, data access, consent/ethics approval, compute budget | Claude cannot hold credentials, spend money, or grant ethics approval |
| H3 | **Results sanity** — human spot-checks a sample of raw outputs (default 30–50 items) | Catches silent pipeline bugs and scoring errors before they become claims |
| H4 | **Main claim** — human approves the contribution sentence and abstract claim | The author is accountable for what the paper claims |
| H5 | **Submit** — human reads the final PDF and clicks submit | Authorship, AI-use disclosure, and author declarations are signed by humans |

Everything not listed here, Claude decides.

## Inbox, not interruptions

Claude never blocks waiting for a reply on a soft question. It writes the question to `research/projects/<slug>/inbox.md`, picks a sensible default, marks it `[DEFAULT TAKEN]`, and keeps going. The human can answer later; Claude applies the answer on the next run and re-does only what it affects.

```markdown
## <date> — <stage> — <short title>   [OPEN | DEFAULT TAKEN | ANSWERED | BLOCKING]
Question:
Default taken (if any):
Impact if changed: <what would need redoing>
Answer:
```

Only H1–H5 items are `BLOCKING`. When a run reaches a blocking item, Claude finishes all work that does not depend on it, then stops and reports.

## Autonomous decision rules

- Prefer the option that is cheapest to reverse.
- Prefer public data and open code; never scrape behind logins or bypass terms of service.
- Use the strongest recent baseline found in the closest-work table, plus one simple baseline.
- Choose the venue by decision-matrix with the human's stated constraints; if none are stated, prefer indexed (Scopus/SCIE) venues with transparent review and no predatory signals.
- Record every autonomous decision in `status.md` gate log with `[AUTO]` and one-line reason.

## Integrity rules (non-negotiable in autopilot)

1. **No fabricated evidence.** Every citation comes from a search tool or the user's library; every number comes from code that ran on real data. If an experiment cannot be run, the paper says so; Claude never writes results it did not compute.
2. **Provenance log.** `research/projects/<slug>/provenance.md` lists, per section, what Claude drafted, what tools produced, and what the human wrote or changed.
3. **AI-use disclosure.** Generate a disclosure statement from the provenance log (tools used, which parts were AI-drafted, what the human verified) and place it where the venue requires. Never omit it.
4. **AI is not an author.** The human authors are listed; Claude is acknowledged as a tool per the venue's policy.
5. **Comprehension brief.** Before H5, produce a 1-page brief and 10 likely reviewer/interview questions with answers, so the human can defend every claim.

## Run report (end of every autopilot run)

At most 10 lines: stages completed, decisions taken `[AUTO]`, open inbox items, blocking checkpoint reached (if any), the exact input needed from the human, and the next stage.
