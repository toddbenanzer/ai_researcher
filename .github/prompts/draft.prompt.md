---
description: Produce a formatted deliverable — email, deck, exec summary, markdown doc, or bullet brief
tools: ["codebase", "editFiles", "createFile"]
---

Produce a formatted deliverable for: ${selectedText}

Only read files within `current-project/`. Do not access any other folder.

Supported output types:
1) Email Draft
2) Deck Slide Content (PowerPoint outline)
3) Executive Summary
4) Markdown Document
5) Word Document Outline
6) Bullet Point Brief
7) Excel Agent Prompt (copy-paste-ready prompt for Excel agent mode)

Follow the Draft Output Mode behavior:
1. Confirm the output type, topic, audience, and tone before starting.
2. Scan the index. Load relevant research files from `current-project/research/`.
3. Produce the output following the format standards in `.github/instructions/output-formats.instructions.md`.
4. Save to `current-project/output/` with the correct filename convention (`YYYY-MM-DD-[output-type]-[short-topic-slug].md`).
5. Confirm the filename to the user after saving.
6. Offer a revision pass if the user wants adjustments.
