---
description: Produce a formatted deliverable — email, deck, exec summary, markdown doc, or bullet brief
tools: ["codebase", "editFiles", "createFile"]
---

Produce a formatted deliverable for: ${selectedText}

Supported output types: Email Draft | Markdown Doc | Deck Slide Content | Executive Summary | Bullet Point Brief

Follow the Draft Output Mode behavior:
1. Confirm the output type and topic before starting.
2. Scan the index. Load relevant research files.
3. Produce the output following the format standards in `.github/instructions/output-formats.instructions.md`.
4. Save to `current-project/output/` with the correct filename convention (`YYYY-MM-DD-[output-type]-[short-topic-slug].md`).
5. Confirm the filename to the user after saving.
6. Offer a revision pass if the user wants adjustments.
