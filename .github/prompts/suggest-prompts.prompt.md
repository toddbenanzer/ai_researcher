---
description: Generate up to 5 ready-to-paste Microsoft Copilot for M365 prompts based on existing research gaps — or starter prompts if no research exists yet.
tools: ["codebase"]
---

Analyze the research in `current-project/research/` and generate up to 5 prompts
I can paste into Microsoft Copilot for Microsoft 365 (copilot.microsoft.com).

Only read files within `current-project/`. Do not access any other folder.

Steps:
1. Check whether any research files exist in `current-project/research/`.

   If research files exist:
   - Scan `current-project/working-files/research-index.md` (or scan research files directly if index is missing)
   - Identify gaps: what angles, data points, or perspectives are missing?
   - Generate up to 5 prompts targeting those specific gaps

   If no research files exist:
   - Ask me for the topic or goal (one question)
   - Generate up to 5 starter prompts to help begin collecting research

2. For each prompt:
   - Write it as a complete, copy-paste-ready sentence or paragraph
   - Label it [Work Mode] or [Web Mode]
     - Work Mode = searches documents, emails, Teams messages, SharePoint
     - Web Mode = searches the public web
   - Add a one-line note on what type of information it surfaces

3. Present as a numbered list. Do not save to output — these are for manual use.

Output format:
## Suggested Microsoft Copilot Prompts

**Research context:** [1-sentence summary or "No existing research — starter prompts below"]
**Identified gaps:** [2–4 bullets]

---
**1. [Work Mode]**
> [prompt]
*Surfaces: [what this finds]*

[continue up to 5]
