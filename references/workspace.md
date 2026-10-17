# Workspace layout

All funnel skills read and write these files. Keep them plain Markdown so any tool can open them.

```
research/
  ideas.md            # central idea bank, all projects (append only)
  reading-log.md      # one 5-line entry per paper read
  projects/
    <slug>/
      status.md       # stage, gates passed, deadlines, next action
      design.md       # study design (stage 4)
      experiments.md  # run log + results table (stage 5)
      venue.md        # venue decision (stage 6)
      draft/          # section files (stage 7)
      reviews/        # pre-submit report, reviewer comments, response letter
      inbox.md        # questions for the human, with defaults taken (autopilot)
      provenance.md   # who/what produced each section (autopilot, for AI-use disclosure)
      code/           # runnable experiment code + RUN_ME.md
```

## status.md template

```markdown
# <Project title>
- Owner:
- One-line question:
- Target venue:            (set at stage 6)
- Deadline:
- Current stage:           1 Idea
- Next action:

## Gate log
| Date | Stage | Decision | Reason |
|---|---|---|---|
```

## ideas.md entry format

```markdown
### <ID> <Short title>  — Novelty <x>/10 — Status: new | testing | chosen | killed
- Problem:
- Angle (what is new):
- Data / feasibility:
- Source project:
- Added: <date>
```

## reading-log.md entry format

```markdown
### <date> — <Authors, Year> — <Title> (<DOI or link>)
1. Problem:
2. Method:
3. Key result (number):
4. Limitation:
5. Use for me:
```
