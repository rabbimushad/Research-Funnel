# Learning-value router

Before every task, decide who does it based on what would build the human's skill and what saves time. Speed and expertise are traded off explicitly, against a daily time budget.

## Three task types

| Type | Who | Rule |
|---|---|---|
| **M — Mechanical** | Claude alone | No research skill is built by doing it: search, dedupe, formatting, citation lookup, templates, logging, boilerplate code, environment setup, figure styling. |
| **G — Growth** | Human attempts first (1–3 lines or one small action), then Claude completes and gives feedback | Doing it builds a core research skill the human has **not yet mastered**. |
| **J — Judgment** | Human decides | Hard checkpoints H1–H5 in `autopilot.md`, plus any choice that changes the paper's claim or the human's time commitment. Always the human, regardless of skill. |

## How to classify a task as G or M

A task is **G** only if all three hold:
1. It exercises a **core skill** (list below).
2. The skill is **not mastered** in `research/learning-log.md` (streak < 4, or never seen).
3. It fits in today's **growth budget**.

Otherwise it is **M**, and Claude does it and attaches a one-line "why" note so the human still sees the reasoning passively.

### Core skills (the base of a strong researcher)

1. Problem framing — turning an interest into a falsifiable question
2. Gap finding — judging what is new against closest work
3. Fast reading — extracting a paper's claim, evidence and limits
4. Study design — baselines, controls, metrics, ablations
5. Statistics — test choice, effect size, uncertainty
6. Threats to validity — leakage, bias, confounds, generalisation
7. Argument writing — contribution statement, intro logic, discussion
8. Critique — spotting weak claims in own and others' work
9. Reviewer response — evidence-based rebuttal

## Growth budget (the time war)

- Default: **30 minutes per day** of human time across all projects. The human can set it ("budget: 15 min", "budget: 60 min").
- Each G task carries an estimate (2–15 min). Fill the budget with the **highest-value** G tasks:
  value = (skill weakness) × (impact on the paper) × (how often the skill recurs).
- G tasks that do not fit become M for today, with a concept card queued for spaced review instead.
- Never let growth tasks block a deadline: if a submission deadline is within 7 days, cap growth at 10 minutes per day and route everything else to M, except J.

## Adaptive promotion and demotion

- After each G task, score the attempt 0–2 and update `learning-log.md`.
- A skill with streak ≥ 4 is **mastered** → its tasks become M (Claude does them; spot-checked once every 5 occurrences with a quick G question to make sure the skill has not faded).
- A mastered skill scoring 0 on a spot-check → back to G.
- A new core skill appearing for the first time → always G once, even on a tight budget.

## Output in run reports

One line per run: `Router: M <n> tasks (Claude), G <n> tasks (<minutes> min, you), J <n> decisions` and the skill currently weakest.
