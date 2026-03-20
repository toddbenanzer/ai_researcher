# AI Researcher — VS Code GitHub Copilot Workspace

A structured research workspace for VS Code GitHub Copilot Chat. Drop your research
files in, and use powerful chat modes to analyze, synthesize, plan, and produce
polished outputs.

---

## Quick Start

1. **Add your research files** to `current-project/research/` (.md or .txt)
2. **Open Copilot Chat** in VS Code
3. **Start a session** — the researcher will automatically index your files
4. **Use slash commands or chat modes** to begin working

---

## Folder Structure

```
current-project/
├── research/        ← Drop your .md and .txt source files here
├── working-files/   ← Auto-generated: index, research notes, session log
└── output/          ← All final deliverables land here
```

---

## Slash Commands

| Command | What it does |
|---|---|
| `/reindex` | Rebuild the research index from scratch |
| `/research [topic]` | Deep research task |
| `/draft [type] [topic]` | Produce a formatted deliverable |
| `/plan [goal]` | Build a structured plan |
| `/summarize [topic or "all"]` | Summarize research content |
| `/review [file or topic]` | Critique and review |
| `/brainstorm [topic]` | Open ideation session |
| `/gap-prompts [topic]` | Generate M365 Copilot prompts to fill research gaps |

---

## Chat Modes

Open a specific mode from the Copilot Chat mode picker:

| Mode | Best for |
|---|---|
| **Brainstorm** | Generating ideas and exploring angles |
| **Write** | Producing polished written content |
| **Summarize** | Condensing research into clear summaries |
| **Plan** | Building structured, actionable plans |
| **Review** | Critiquing and improving documents |
| **Deep Research** | Thorough multi-file research and synthesis |
| **Draft Output** | Creating specific deliverables (email, deck, summary, etc.) |
| **Research Gap Prompts** | Identify research gaps and generate M365 Copilot prompts to fill them |

---

## Gathering Additional Research with M365 Copilot

Use **Research Gap Prompts** mode (or `/gap-prompts`) when your research feels incomplete and you want to pull in more information from enterprise sources or the web.

**The workflow:**
1. Run `/gap-prompts` or switch to **Research Gap Prompts** mode
2. The tool analyzes your existing research and identifies gaps
3. It generates ready-to-paste prompts for **Microsoft 365 Copilot**, each labeled with the correct mode:
   - **🏢 Work Mode** — searches your emails, Teams messages, OneNote, SharePoint, and internal docs
   - **🌐 Web Mode** — searches the internet for current data, news, and published research
4. Paste each prompt into [M365 Copilot](https://m365.cloud.microsoft/chat), select the indicated mode, and ask it to format its response as a markdown document
5. Save the markdown response into `current-project/research/`
6. Run `/reindex` to update the index
7. Continue with **Deep Research** or **Summarize** mode to incorporate the new material

---

## Output Types (Draft Output Mode)

- Email Draft
- Markdown Doc (shareable/peer-ready)
- Deck Slide Content (markdown formatted for PowerPoint/Slides)
- Executive Summary
- Bullet Point Brief

---

## Knowledge Boundaries

The researcher prioritizes your research folder content. If it supplements with
general knowledge, it will flag it explicitly with `[General Knowledge]`.

---

## Default Model

**gpt-4.5** (latest) across all chat modes.
