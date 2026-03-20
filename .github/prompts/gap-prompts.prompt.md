---
description: Analyze research gaps and generate ready-to-paste Microsoft 365 Copilot prompts (web or work mode)
tools: ["codebase", "editFiles", "createFile"]
---

Analyze the current research for gaps and generate Microsoft 365 Copilot prompts to fill them.
Focus area (if specified): ${selectedText}

Follow these steps:

1. **Index Check** — Read `current-project/working-files/research-index.md`. If it appears stale or empty, stop and ask the user to run `/reindex` first.

2. **Read Research** — Read all files in `current-project/research/` relevant to the focus area (or all files if no focus is specified).

3. **Identify the Top 5 Gaps** — Look for:
   - Topics mentioned but not deeply covered
   - Questions raised but not answered
   - Claims made without supporting sources
   - Areas needing internal enterprise data (emails, Teams, OneNote, SharePoint)
   - Areas needing current external data (news, market trends, published research)

4. **Classify Each Gap** as one of:
   - **🌐 Web Mode** — needs current internet sources (news, market data, industry trends, public research)
   - **🏢 Work Mode** — needs internal enterprise sources (emails, Teams messages, OneNote, SharePoint, internal docs)

5. **Generate one polished, copy-paste-ready M365 Copilot prompt per gap** using this format:

---

## Prompt [N]: [Short Gap Title]

**Gap identified:** [1–2 sentences on what is missing]
**Coverage status:** [Missing / Thin / Unconfirmed / Needs internal sources / Needs current data]
**Recommended M365 Copilot Mode:** 🌐 Web Mode OR 🏢 Work Mode

**Paste this prompt into M365 Copilot:**

```
[Ready-to-paste prompt — see rules below]
```

**Save the response as:** `[YYYY-MM-DD]-gap-research-[slug].md` → drop into `current-project/research/`

---

**Rules for writing 🏢 Work Mode prompts:**
- Tell Copilot to search: emails, Microsoft Teams chat messages, OneNote notebooks, SharePoint documents, and internal documentation
- Ask it to look for decisions, discussions, meeting notes, policies, and shared files on the topic
- Ask it to cite the source type (email, Teams, OneNote, SharePoint) for each finding
- End with: "Format your response as a markdown document with a summary section and findings organized by theme."

**Rules for writing 🌐 Web Mode prompts:**
- Specify the type of source needed (industry reports, news, published research, statistics)
- Include a recency requirement if needed ("published in the last 12 months")
- Ask for source URLs or citations
- End with: "Format your response as a markdown document with a summary section and sources cited."

6. **Save output** to `current-project/output/YYYY-MM-DD-gap-prompts-[topic-slug].md`

7. **Close with the return workflow reminder:**
   > **Next steps:** Paste each prompt into M365 Copilot at https://m365.cloud.microsoft/chat, select the correct mode (Web or Work), ask Copilot to format its response as markdown, save results to `current-project/research/`, then run `/reindex`.

8. **Update** `current-project/working-files/session-log.md` with a new entry for this session.
