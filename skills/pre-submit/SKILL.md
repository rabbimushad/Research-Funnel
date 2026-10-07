---
name: pre-submit
description: Final quality gate before submitting a paper: mock referee review, citation verification, numbers check, venue checklist, and a ranked fix list. Use when the user says "my draft is ready", "review my paper before I submit", "is this ready to submit", "pre-submission check", or "what would reviewers say". Funnel stage 8.
---

# Pre-Submit (Stage 8)

Read at the plugin root: `gates.md`, `skill-map.md`.

## Steps

1. **Attempt first.** Ask the user to name the 2 weaknesses they expect reviewers to attack. Record them.
2. **Referee review.** Invoke **paper-critique** on the draft, telling it the target venue from `venue.md`. Keep its severity ranking and fixes.
3. **Citation check.** Invoke **citation-check** on the draft and reference list.
4. **Numbers check.** Every number in abstract, text and tables matches `experiments.md` (if it exists; otherwise ask the user for the source of each headline number).
5. **Venue checklist.** Template, page limit, anonymisation, data/code availability, ethics, author contributions, funding, COI, cover letter.
6. **Compare** the critique's top issues with the user's 2 predictions; say what they missed.
7. Write `projects/<slug>/reviews/pre-submit.md`.
8. **GATE 8 — Submit or fix.** Recommend with estimated hours. The user fixes major issues themselves. Never mark ready while any reference is unverified or a number mismatches. Log in `status.md`.

## Entering mid-funnel

If the user arrives here with an existing draft and no project, create `projects/<slug>/status.md` from the draft, mark stages 1–7 as "pre-funnel", and run this stage.
