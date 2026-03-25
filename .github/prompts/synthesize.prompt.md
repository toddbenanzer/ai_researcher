---
description: Pull all research files into one comprehensive, unified narrative document — not a list of per-file summaries, but a single integrated synthesis.
tools: ["codebase", "editFiles", "createFile"]
---

Read every file in `current-project/research/` and produce one comprehensive,
unified synthesis document.

Only read files within `current-project/`. Do not access any other folder.

This is different from /summarize:
- /summarize = short TL;DR per document
- /synthesize = one integrated narrative across all documents

Steps:
1. Verify or rebuild the research index at `current-project/working-files/research-index.md`.
2. State your plan: list all files you will read.
3. Read every file in `current-project/research/` fully.
4. Identify major themes, key findings, contradictions between sources, and gaps.
5. Write a single coherent narrative document — not a collection of summaries.
   Integrate findings across sources without attributing every sentence to a file
   unless the source distinction is meaningful.
6. Flag anything from general knowledge: [General Knowledge]
7. Save to `current-project/output/` as `YYYY-MM-DD-synthesis-[topic-slug].md`.
8. Update `current-project/working-files/session-log.md`.

Document structure:
- Executive Overview (3–5 sentences: what the research collectively tells us)
- Background and Context
- Key Themes and Findings (H3 per theme, narrative prose)
- Points of Tension or Contradiction
- What the Research Does Not Cover
- Conclusions
- Recommended Next Steps
