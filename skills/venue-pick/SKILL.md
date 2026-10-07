---
name: venue-pick
description: Choose the right journal or conference for a paper using a weighted comparison of scope fit, quartile/ranking, review time, acceptance rate, open-access cost, and deadline. Use when the user says "where should I submit", "which journal", "Q1 or Q2", "conference or journal", or "find a venue for my paper". Funnel stage 6.
---

# Venue Pick (Stage 6)

Read at the plugin root: `gates.md`, `skill-map.md`.

## Steps

1. **Attempt first.** Ask for 1–3 venues the user has in mind and hard constraints (deadline, APC budget, indexing such as Scopus/SCIE, quartile target).
2. Candidates: venues where closest-work papers were published + the user's picks (4–6).
3. Look up current facts by web search: scope, quartile (SJR/JCR), time to first decision, APC, next deadline, page limit, template. Cite; mark gaps. Never from memory.
4. Invoke **decision-matrix** with these options and criteria: scope fit (×3), quartile vs target (×2), speed (×2), cost (×1), deadline fit (×2).
5. Flag predatory signals (unrealistic review speed, missing indexing, spam invitations).
6. **GATE 6 — Choose venue + fallback.** Write `projects/<slug>/venue.md` (decision, template, page limit, deadline, fallback). Log in `status.md`.
