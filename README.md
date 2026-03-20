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
