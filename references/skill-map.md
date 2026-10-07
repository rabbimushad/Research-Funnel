# Skill map — which validated skill each stage calls

The funnel does not redo work that a validated skill already does well. Each stage **invokes the named skill with the Skill tool**, then adds only the funnel layer: attempt-first, gate, logging, idea bank.

Skill names differ slightly between installs (with or without a plugin prefix). Match by the short name; if two match, prefer the one with the prefix shown.

| Short name | Typical full name | Used in stage |
|---|---|---|
| fasttrack-topic-validator | anthropic-skills:fasttrack-topic-validator | 1 Idea, 2 Gap check |
| paper-search | paper-search:paper-search | 2, 3 |
| literature-review-helper | anthropic-skills:literature-review-helper | 2 (lit map), 7 |
| research-litnote | research-desk:research-litnote | 3 Reading |
| read-paper | read-paper:read-paper | 3 (key papers, deep read) |
| paper-compare | research-desk:paper-compare | 3, 4 (baseline choice) |
| decision-matrix | research-desk:decision-matrix | 6 Venue, any A-vs-B choice |
| related-work | research-desk:related-work | 7 Drafting |
| academic-document-writer | anthropic-skills:academic-document-writer | 7 Drafting |
| paper-critique | research-desk:paper-critique | 4 (design review), 8 Pre-submit |
| citation-check | research-desk:citation-check | 8 Pre-submit, 9 Revision |
| llm-council | research-desk:llm-council | Any high-stakes gate (kill an idea, final claim, rebuttal stance) |
| deep-research | anthropic-skills:deep-research | 2 (broad landscape), PhD lab scans |
| research-proposal | research-proposal | PhD proposal (optional install) |

Connectors used directly when present: Consensus, SciSpace, PubMed, web search.

## Fallback rule

If a named skill is not installed, do the step directly using the same intent described in the stage, say in one line which skill is missing, and suggest installing it (Research Desk plugin covers most of them).

## Hand-off rule

1. Tell the user in one line which skill is running and why.
2. Pass it the project context (question, files, venue).
3. Take its output, then run the funnel layer: compare with the user's attempt, write the GATE block, log the decision.
