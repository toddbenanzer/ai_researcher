---
applyTo: "**"
---

# Research Indexing Protocol

## What the Index Is
The research index is a single reference file at:
`current-project/working-files/research-index.md`

It provides a structured, scannable map of all research files so the assistant can
quickly determine which files are relevant to any given task without loading all
files into context simultaneously.

## Index Structure
Each entry in the index must include:
- **Filename** — relative path from repo root
- **File type** — .md or .txt
- **Title or topic** — inferred from the first heading or first line
- **Summary** — 2–3 sentence description of the file's content
- **Key themes/tags** — 3–6 keywords that describe the content
- **Last indexed** — date the entry was created or updated

### Example entry:
```
### current-project/research/competitive-landscape.md
- **Type:** .md
- **Topic:** Competitive Landscape Analysis
- **Summary:** Covers the top 5 competitors in the deposits space, their product
  offerings, digital capabilities, and pricing structures as of Q1 2025.
- **Tags:** competitors, deposits, digital banking, pricing, market share
- **Last indexed:** 2025-06-01
```

## Indexing Protocol (Session Start)
1. Scan all `.md` and `.txt` files in `current-project/research/`.
2. For each file, read it and produce an index entry in the format above.
3. Write all entries to `current-project/working-files/research-index.md`,
   overwriting any previous version.
4. Report to the user: number of files indexed and confirm the index is ready.

## /reindex Command
When the user types `/reindex`:
1. Delete the existing `research-index.md` content.
2. Re-scan all files in `current-project/research/`.
3. Rebuild the index from scratch.
4. Confirm completion and file count to the user.

## Using the Index During Tasks
Before pulling any full research file into context:
1. Read `research-index.md` first.
2. Identify which files are relevant based on tags and summaries.
3. Load only those files.
4. State to the user which files you are referencing and why.
