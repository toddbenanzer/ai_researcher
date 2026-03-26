---
description: Rebuild the research index from scratch by scanning all research files
tools: ["codebase", "editFiles", "createFile"]
---

Rebuild the research index from scratch following the indexing protocol in
`.github/instructions/indexing.instructions.md`.

Only read files within `current-project/`. Do not access any other folder.

Steps:
1. Delete all existing content in `current-project/working-files/research-index.md`.
2. Scan all `.md` and `.txt` files in `current-project/research/`.
3. Read each file and produce an index entry with all required fields:
   - **Filename** — relative path from repo root
   - **File type** — .md or .txt
   - **Topic** — inferred from the first heading or first line
   - **Summary** — 2–3 sentence description of the file's content
   - **Tags** — 3–6 keywords describing the content
   - **Last indexed** — today's date
4. Write all entries to `current-project/working-files/research-index.md`,
   replacing the previous version entirely.
5. If `current-project/research/` is empty or missing, report that to the user
   and do not create a blank index.
6. Confirm completion to the user: state the number of files indexed and list
   any files that could not be read or parsed.
7. Update `current-project/working-files/session-log.md` with the reindex task.
