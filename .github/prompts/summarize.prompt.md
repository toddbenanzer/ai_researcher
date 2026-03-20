---
description: Summarize research content — a specific file, topic, or all research
tools: ["codebase", "editFiles", "createFile"]
---

Summarize the following (file, topic, or "all"): ${selectedText}

Follow the Summarize Mode behavior:
- If summarizing a specific file: load it, read fully, produce a structured summary.
- If summarizing a topic: scan the index, load relevant files, synthesize across them.
- If summarizing "all": produce a master summary of the entire research folder, organized by theme.
- Always state how many files / sources were used.

Output structure:
- **TL;DR** (1–2 sentences at the top)
- **Key Points** (5–7 bullets)
- **Detail Section** (organized by theme if multi-file)
- **Gaps / Open Questions** (what the research does NOT cover)
