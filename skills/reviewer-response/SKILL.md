---
name: reviewer-response
description: Handle peer-review decisions: parse reviewer comments, plan revisions, and draft a point-by-point response letter; or redirect a rejected paper to the next venue. Use when the user says "I got reviews", "major revision", "minor revision", "write a rebuttal", "respond to reviewers", or "my paper was rejected". Funnel stage 9.
---

# Reviewer Response (Stage 9)

Read at the plugin root: `gates.md`, `skill-map.md`.

## Revision path

1. Save the decision letter to `projects/<slug>/reviews/`.
2. Split comments into atomic items (R1.1, R2.3…). Classify: must-do / should-do / disagree-with-evidence / clarify-only. Estimate effort.
3. **Attempt first.** For each must-do, ask how the user plans to address it.
4. For any item where you would push back on a reviewer, invoke **llm-council** to test the stance before committing.
5. Revision table: item, change, location, status.
6. Draft the response letter: per item quote, change, page/line. Polite, evidence-based.
7. After revisions, invoke **citation-check** on any new references and **paper-critique** on changed sections.
8. **GATE 9 — Approve letter and changes.** Cross-check every promised change appears. Log in `status.md`.

## Rejection path

Extract ≤5 fixable lessons, hand off to venue-pick with the fallback venue, set a resubmission date within 3 weeks, log it.
