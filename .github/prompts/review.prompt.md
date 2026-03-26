---
description: Critically review and improve a document, argument, or plan
tools: ["codebase", "editFiles", "createFile"]
---

Review the following file or topic: ${selectedText}

Only read files within `current-project/`. Do not access any other folder.

Steps:
1. Read the document or content to be reviewed in full before making any comments.
2. Check the research index at `current-project/working-files/research-index.md`
   to identify relevant research files that can serve as reference points.
3. Cross-reference claims, data, and assertions against relevant research files.
   Note where the document aligns with, contradicts, or goes beyond the available
   research.
4. Evaluate the document on three dimensions:
   - **Clarity** — Is the structure logical? Is the writing concise and scannable?
   - **Accuracy** — Are claims supported by the research? Are there factual errors?
   - **Completeness** — Are important aspects of the topic missing or underexplored?
5. Structure feedback as specific, actionable suggestions — do not just list
   problems without offering solutions or alternative language.
6. Save the review to `current-project/output/` using the naming convention
   `YYYY-MM-DD-review-[document-slug].md`.
7. Update `current-project/working-files/session-log.md` with the completed task.

Review output structure:
- **Overall Assessment** — 2–3 sentences summarizing the document's current state
  and readiness
- **Strengths** — what works well (be specific, cite sections or lines)
- **Issues** — organized by severity:
  - *Critical* — factual errors, missing key content, structural problems that
    undermine the document's purpose
  - *Important* — weak arguments, unsupported claims, unclear sections
  - *Minor* — tone, word choice, formatting, polish
- **Suggested Revisions** — specific, actionable changes with proposed rewrites
  where helpful
- **Quality Scores:** Clarity [x/5] | Accuracy [x/5] | Completeness [x/5]
- **Sources Referenced** — list any research files used for cross-referencing

If the document references topics not covered in the research folder, note those
gaps rather than evaluating claims you cannot verify. Flag any general knowledge
used with `[General Knowledge]`.
