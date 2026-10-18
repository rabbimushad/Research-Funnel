# Speed-read map

Every paper Claude suggests comes with a reading map, so the human gets most of the value in the least time and reads only the parts that build their project or their skill.

## Triage tiers

| Tier | Time | When |
|---|---|---|
| **Skip** | 0 min (summary only) | Background or tangential; the 3-line summary is enough |
| **Skim** | 5 min | Useful context; read abstract claim + 1 figure/table |
| **Targeted** | 10–20 min | Closest work, baseline source, or method to reuse; read 2–4 named parts |
| **Deep** | 30–45 min | Foundational for the project or teaches a core skill the human is weak in; read full method + results |

Aim: no more than 1 Deep paper per week per project. Most papers should be Skip or Skim.

## Map format (always this shape, max ~15 lines)

```markdown
### <Authors, Year> — <Title> (<DOI/link>)
**Tier:** Targeted · **Time:** 15 min · **Why for you:** <one line: project link and/or skill it builds>

**3-line summary**
1. Problem + claim:
2. Method (one line, plain words):
3. Key result (number) + main limitation:

**Read only these** (in this order)
1. <Section/Figure/Table, page> — *answer:* <question to hold while reading>
2. <…> — *answer:* <…>
3. <…> — *answer:* <…>

**Skip:** <sections safe to skip and why, e.g. "Sec 2 related work — already covered by X">

**After reading (1 min):** write the one line *"Use for me: …"*
```

## Rules

- The summary and page/section pointers must come from the actual paper text (read via PDF, open-access full text, or an abstract-only source clearly marked "abstract only — pointers are estimates").
- Questions to hold while reading are **active-reading prompts**: each targets the claim, evidence, or limitation the human needs, never trivia.
- Prefer figures and tables over prose: a results table often carries the paper in 2 minutes.
- If the paper teaches a core skill the human is weak in (see `router.md` and `learning-log.md`), point to the exact part that teaches it and name the skill.
- After the human reads, the "Use for me" line is their attempt (a G task). Claude completes the 5-line reading-log entry and notes in at most 2 bullets anything they missed.

## Weekly reading plan

When asked "reading plan" or at the start of a project, propose 5–8 papers for the week ordered by value, each with tier and time, total within the human's reading budget (default 90 minutes per week).
