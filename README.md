# Research Funnel

A complete research workflow from first idea to published paper. Claude does the searching, logging, formatting and checking. You make every decision that shapes the research, at a gate at the end of each stage.

## Start here

Say **"start research"** (or run `/research-start`). Claude sets up a `research/` folder, finds where your project is, and names one next action.

## The 9 stages

| # | Stage | Say this | You decide at the gate |
|---|---|---|---|
| 1 | Idea | "give me research ideas on X" | Which idea to pursue |
| 2 | Gap check | "has this been done?" | Go / pivot / kill |
| 3 | Reading | "what should I read next" / "log this paper" | (daily habit) |
| 4 | Study design | "design my study" | Question, data, baselines, metrics |
| 5 | Experiments | "log this run" / "make the results table" | Ready to write? |
| 6 | Venue | "which journal should I submit to" | Target venue |
| 7 | Drafting | "draft the methods section" | Approve each section |
| 8 | Pre-submit | "my draft is ready" | Submit or fix first |
| 9 | Revision | "I got reviews" | Approve response letter |

## Three rules that make it work

1. **Attempt first.** At each gate, Claude asks for your own answer before showing its own. This is how you build research judgment.
2. **No invented evidence.** Papers, numbers and references come only from search tools, your files, or you.
3. **Everything is logged.** `status.md` per project records every gate decision, so you or a collaborator can pick up anywhere.

## Your files

```
research/
  ideas.md         central idea bank across all projects, with novelty scores
  reading-log.md   5-line summary per paper
  projects/<name>/ status, design, experiments, venue, draft, reviews
```

## Built on validated skills

The funnel does not reinvent search, notes, critique or citation checks. Each stage calls an existing validated skill and adds the human gate and logging on top:

| Stage | Calls |
|---|---|
| Idea, Gap check | fasttrack-topic-validator, paper-search, literature-review-helper, llm-council |
| Reading | paper-search, research-litnote, read-paper, paper-compare |
| Study design | paper-compare, paper-critique |
| Venue | decision-matrix |
| Drafting | related-work, academic-document-writer |
| Pre-submit | paper-critique, citation-check |
| Revision | llm-council, citation-check, paper-critique |

Missing a skill? The stage falls back to doing the step directly and tells you what to install (most come with the Research Desk plugin).

## Works best with

Academic search connectors (Consensus, SciSpace, PubMed) or a paper-search plugin, plus web search. Optional companion skills it hands off to when installed: paper-critique, citation-check, related-work, research-litnote, read-paper.

## Install

**Claude desktop app (Cowork / Claude Code):** download this repo as a ZIP, rename it to `research-funnel.plugin`, and open it in Claude — or add it as a plugin marketplace source in Claude Code:

```
/plugin marketplace add rabbimushad/research-funnel
/plugin install research-funnel@research-funnel
```

Then say **"start research"**.

## License

MIT
