---
description: Run a deep research task on a topic using research folder content
tools: ["codebase", "editFiles", "createFile"]
---

Run a deep research task on the topic: ${selectedText}

Only read files within `current-project/`. Do not access any other folder.

Steps:
1. Verify the research index at `current-project/working-files/research-index.md`
   is current. If stale or missing, rebuild it first using the indexing protocol
   in `.github/instructions/indexing.instructions.md`.
2. Scan the index. Identify ALL files with any relevance to the topic — err on
   the side of inclusion.
3. State your research plan to the user: which files you will read, in what
   order, and why each is relevant.
4. Read each relevant file fully. Take structured notes in
   `current-project/working-files/research-notes.md` organized by file, capturing
   key facts, data points, and quotes relevant to the topic.
5. Synthesize findings across files:
   - Identify patterns and recurring themes
   - Flag contradictions between sources
   - Note gaps where the research folder lacks coverage
6. Produce a structured Research Report and save it to `current-project/output/`
   using the naming convention `YYYY-MM-DD-research-[topic-slug].md`.
7. Flag anything supplemented from general knowledge with
   `[General Knowledge]` inline.
8. Update `current-project/working-files/session-log.md` with the completed task.

Research Report structure:
- **Research Question** — the topic restated as a clear question or objective
- **Sources Consulted** — list of research files read, with brief relevance note
- **Key Findings** (H3 per finding, with supporting evidence from files)
- **Cross-Source Patterns** — themes that appear across multiple files
- **Contradictions or Tensions** — where sources disagree or conflict
- **Gaps in Available Research** — what the folder does not cover
- **Conclusions and Implications**
- **Suggested Next Steps** — follow-up research, questions to explore, or actions

If the research folder contains insufficient material to meaningfully address the
topic, state that clearly before proceeding. Do not fabricate findings.
