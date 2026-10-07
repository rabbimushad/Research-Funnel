---
name: draft-paper
description: Draft a research paper section by section for a chosen venue, with the human writing the core claims and approving each section. Use when the user says "start writing my paper", "draft the introduction", "write the methods", "write related work", "write the abstract", or "outline my paper". Funnel stage 7.
---

# Draft Paper (Stage 7)

Read at the plugin root: `gates.md`, `skill-map.md`.

## Order

1. **Outline** sized to the page limit in `venue.md`; 2–3 claims per section.
2. **Methods, Experiments, Results** — from `design.md` and `experiments.md`. Invoke **academic-document-writer** for these sections (real APA citations via Consensus, human-sounding prose). If the venue needs IEEE/ACM style, convert citation style afterward.
3. **Related work** — invoke **related-work** with the reading log, closest-work table, and the user's sources only. It ends on the gap; check the gap matches the contribution claim.
4. **Introduction** — the user writes the contribution paragraph first; then invoke **academic-document-writer** to build around it.
5. **Discussion, limitations, conclusion** — academic-document-writer.
6. **Abstract last** — the user writes the main-claim sentence.

Save sections to `projects/<slug>/draft/`.

## Per-section gate

After each section: list claims still lacking a citation or number; ask approve/change. Do not move on until approved.

## Rules

- Every number matches `experiments.md`. No invented references.
- No hype words ("revolutionary", "delves", "pivotal role"). Hedge to evidence.
