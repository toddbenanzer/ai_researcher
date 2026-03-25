# AI Researcher — VS Code GitHub Copilot Workspace

A structured research workspace for VS Code GitHub Copilot Chat. Drop your research
files in, use the guided workflow to collect, summarize, and synthesize your research,
then produce polished outputs in any format.

---

## Quick Start

1. **Add your research files** to `current-project/research/` (.md or .txt)
2. **Open Copilot Chat** in VS Code
3. **Use Workflow mode** to walk through all stages end-to-end, or pick any individual mode below

---

## Recommended Workflow

The system is designed around four sequential stages. Use **Workflow** mode to be
guided through all of them, or run each stage independently.

```
Stage 1: Collect & Index Research
         Drop .md / .txt files into current-project/research/ and run /reindex
         ↓
Stage 2: Suggest Additional Prompts  [optional utility]
         Use Suggest Prompts mode to identify gaps and generate prompts
         to run in Microsoft Copilot for M365 (Work Mode or Web Mode)
         ↓
Stage 3: Summarize
         Per-document TL;DRs saved to current-project/working-files/research-summaries.md
         ↓
Stage 4: Synthesize
         One comprehensive unified narrative saved to current-project/output/
         ↓
Stage 5: Write Output
         Produce a deliverable in your chosen format
```

---

## Folder Structure

```
current-project/
├── research/        ← Drop your .md and .txt source files here
├── working-files/   ← Auto-generated: index, research notes, summaries, session log
└── output/          ← All final deliverables land here
```

**Scope:** All modes and commands only read files within `current-project/`.
Files outside this folder (archive folders, old projects, etc.) are never accessed.

---

## Chat Modes

Open a mode from the Copilot Chat mode picker:

| Mode | What it does |
|---|---|
| **Workflow** | Guided end-to-end walkthrough of all four stages |
| **Suggest Prompts** | Reads existing research and generates up to 5 prompts to run in Microsoft Copilot for M365 (labeled Work Mode or Web Mode) |
| **Summarize** | Per-document TL;DRs — what does each file say? |
| **Synthesize** | One comprehensive unified narrative across all research |
| **Draft Output** | Produce a specific formatted deliverable |
| **Write** | Polished written content with full format menu |
| **Deep Research** | Thorough multi-file research analysis with structured report |
| **Plan** | Build structured, actionable plans |
| **Brainstorm** | Ideation and angle exploration |
| **Review** | Critique and improve documents |

---

## Slash Commands

| Command | What it does |
|---|---|
| `/reindex` | Rebuild the research index from scratch |
| `/suggest-prompts` | Generate M365 Copilot prompts based on research gaps |
| `/summarize [topic or "all"]` | Summarize research content |
| `/synthesize` | Create a comprehensive unified research narrative |
| `/draft [type] [topic]` | Produce a formatted deliverable |
| `/research [topic]` | Deep research task |
| `/plan [goal]` | Build a structured plan |
| `/review [file or topic]` | Critique and review |
| `/brainstorm [topic]` | Open ideation session |

---

## Output Types

All outputs save to `current-project/output/` with naming `YYYY-MM-DD-[type]-[topic].md`.

| Format | Best for |
|---|---|
| Email Draft | Stakeholder communications |
| Deck Slide Content | PowerPoint / Google Slides (maps 1:1 to slides) |
| Executive Summary | Senior audience, max 1 page |
| Markdown Document | Shareable peer-ready docs (Confluence, Notion, etc.) |
| Word Document Outline | Structured outline to paste into Word and author |
| Bullet Point Brief | Quick-consumption briefs |
| Excel Agent Prompt | Copy-paste prompt for Microsoft Excel agent mode |

---

## Suggest Prompts — Microsoft Copilot for M365

The **Suggest Prompts** mode generates prompts you copy and paste into
[copilot.microsoft.com](https://copilot.microsoft.com). Each prompt is labeled:

- **[Work Mode]** — searches your documents, emails, Teams messages, and SharePoint
- **[Web Mode]** — searches the public web

Can be used before you have any research (generates starter prompts) or after
collecting research (identifies gaps and generates targeted follow-up prompts).

---

## Knowledge Boundaries

All modes prioritize files in `current-project/research/`. If a mode supplements
with general knowledge, it flags it explicitly: `[General Knowledge]`.

---

## Default Model

**gpt-4.5** (latest) across all chat modes.
