# Learn mode — fast learning inside autopilot

Goal: the human builds a strong research base in the least time. Autopilot does the work; learn checks make sure the human *understands* every decision that shapes the paper. On by default in autopilot.

Design principles (why it is fast):
- **Retrieval beats re-reading.** The human answers before seeing the explanation.
- **Only decision-level concepts.** Ask about choices that shape the research, never trivia.
- **Adaptive.** Strong answers shrink the check; weak answers trigger a short lesson.
- **Spaced review.** Missed concepts come back on a schedule, so they stick.
- **Hard time cap:** 3 minutes per stage.

## Learn check (end of every autopilot stage)

1. Pick the **3 highest-leverage questions** from the stage's decisions, one of each type:
   - **Why** — "Why this baseline / dataset / venue / metric?"
   - **What-if** — "What breaks if X changes?" (e.g., data leakage, a different metric, a null result)
   - **Explain** — "Explain [core concept] in 2 lines" (e.g., effect size, mixed-effects model, inter-rater agreement)
2. Ask all 3 at once. The human replies with one line each.
3. Score each 0–2 (0 wrong/blank, 1 partial, 2 correct and specific). Total /6.
4. Feedback, at most 5 lines total:
   - The model answer for anything scored below 2.
   - One **concept card** for the weakest item: definition (1 line), analogy (1 line, in the human's preferred language if known), how it shows up in *this* paper (1 line).
5. **Adapt:**
   - 5–6/6: pass. If the same question type scores ≥5 two stages in a row, ask only 1 question of that type next time.
   - 3–4/6: pass; add missed concepts to review.
   - 0–2/6: give a mini-lesson (≤150 words) on the weakest concept, then 1 retry question. Then continue.
6. Log every concept in `research/learning-log.md`.

Learn checks do not change any research decision unless the human's answer reveals a real problem with it; in that case, record it in `inbox.md` and re-evaluate the decision.

## Blocking or queued

- **Default `learn: on`** — the pipeline waits for answers before starting the next stage. All independent work for the current stage is already finished, so the wait costs no compute.
- **`learn: queue`** — the check goes to `inbox.md`; the pipeline continues. Unanswered checks are asked at the start of the next run.
- **`learn: off`** — only for papers the human explicitly marks as non-core. Not recommended.

## Spaced review

`research/learning-log.md` format:

```markdown
| Concept | Project | Stage | Score | Last seen | Next review | Streak |
|---|---|---|---|---|---|---|
```

- Schedule after a miss or partial: +1 day, +3, +7, +21. A full score advances one step; a miss resets to +1.
- At the start of every run (autopilot or guided), ask up to **2 due review questions** first (≤1 minute), then continue.
- A concept with streak ≥4 is **mastered** and drops out of review.

## Defense drill (before hard checkpoint H5 Submit)

1. Generate 10 likely reviewer / PhD-interview questions about the paper (claim, design, stats, limitations, novelty vs closest work).
2. The human answers in 1–2 lines each; score 0–2.
3. ≥14/20: ready to defend. Below 14: give model answers for misses and recommend a re-drill of the misses before submitting.
4. Save to `projects/<slug>/reviews/defense-drill.md`.

## Progress report

When asked "learning status" (or in each run report), show in at most 4 lines: concepts mastered, concepts due, average learn-check score over the last 5 stages, weakest area.
