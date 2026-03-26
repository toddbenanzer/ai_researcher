# AI Researcher — VS Code GitHub Copilot Workspace

A structured research workspace for VS Code GitHub Copilot Chat. Drop your research
files in, run the guided workflow to collect, index, summarize, and synthesize everything,
then produce polished deliverables in any format.

---

## Table of Contents

1. [What This Is](#what-this-is)
2. [Prerequisites](#prerequisites)
3. [Setup](#setup)
4. [Folder Structure](#folder-structure)
5. [The Research Workflow](#the-research-workflow)
6. [Chat Modes](#chat-modes)
   - [Workflow](#workflow-mode)
   - [Summarize](#summarize-mode)
   - [Synthesize](#synthesize-mode)
   - [Draft Output](#draft-output-mode)
   - [Write](#write-mode)
   - [Deep Research](#deep-research-mode)
   - [Suggest Prompts](#suggest-prompts-mode)
   - [Plan](#plan-mode)
   - [Brainstorm](#brainstorm-mode)
   - [Review](#review-mode)
7. [Slash Commands](#slash-commands)
8. [Output Types](#output-types)
9. [Research Index](#research-index)
10. [Knowledge Boundaries](#knowledge-boundaries)
11. [Writing Style Standards](#writing-style-standards)
12. [Working Files Reference](#working-files-reference)
13. [File Naming Convention](#file-naming-convention)
14. [Tips and Best Practices](#tips-and-best-practices)

---

## What This Is

AI Researcher is a **configuration-driven research workflow system** built on top of
VS Code GitHub Copilot Chat. It is not a Python package or a code library — it is a
set of instruction files, prompt templates, and chat mode definitions that turn Copilot
Chat into a structured research assistant.

The system guides you from raw notes and source files all the way to finished
deliverables: emails, executive summaries, slide decks, reports, and more.

**What it solves:**

- Research scattered across many files with no clear structure
- Difficulty knowing which files are relevant to a given task
- Time lost reformatting the same information for different audiences
- Inconsistent writing style across deliverables

**What it provides:**

- A five-stage workflow from raw files to polished output
- Ten specialized chat modes, each optimized for a specific task
- Nine slash commands for direct task invocation
- Seven output format standards with consistent rules
- An auto-maintained research index so the assistant always knows what you have
- Strict scope enforcement — the assistant only touches files in `current-project/`

---

## Prerequisites

- **VS Code** with the **GitHub Copilot Chat** extension installed and activated
- A GitHub Copilot subscription (Individual, Business, or Enterprise)
- For the Suggest Prompts feature: access to **Microsoft Copilot for M365**
  at [copilot.microsoft.com](https://copilot.microsoft.com) (optional)

---

## Setup

1. **Clone this repository** into VS Code.

2. **Open VS Code** in the repository root. The `.vscode/settings.json` file
   automatically enables instruction files and prompt files for Copilot Chat:

   ```json
   {
     "github.copilot.chat.codeGeneration.useInstructionFiles": true,
     "chat.instructionsFilesLocations": { ".github/instructions": true },
     "chat.promptFilesLocations": { ".github/prompts": true },
     "chat.includeApplyingInstructions": true
   }
   ```

3. **Create your project folder** at the repository root:

   ```
   current-project/
   ├── research/
   ├── working-files/
   └── output/
   ```

4. **Add research files** to `current-project/research/`. Supported formats: `.md` and `.txt`.

5. **Open Copilot Chat** and select a mode from the mode picker, or type a slash command.

---

## Folder Structure

```
current-project/
├── research/
│   ├── my-notes.md
│   ├── competitor-analysis.txt
│   └── ...                        ← your source files (.md and .txt only)
├── working-files/
│   ├── research-index.md          ← auto-generated map of all research files
│   ├── research-notes.md          ← significant findings logged during tasks
│   ├── research-summaries.md      ← per-document TL;DRs (Stage 3 output)
│   └── session-log.md             ← audit trail of completed tasks
└── output/
    ├── 2026-03-26-synthesis-market-trends.md
    ├── 2026-03-26-email-draft-stakeholder-update.md
    └── ...                        ← all final deliverables land here
```

**Scope rule:** All modes and commands only read files within `current-project/`.
The `.copilotignore` file enforces this — files outside this folder are never accessed,
including archive folders, old project folders, or anything else at the repository root.

---

## The Research Workflow

The system is built around five sequential stages. Use **Workflow mode** to be guided
through all of them, or jump directly to any individual stage.

```
Stage 1: Collect & Index Research
         Drop .md / .txt files into current-project/research/
         Assistant scans and builds research-index.md
         ↓
Stage 2: Suggest Additional Prompts  [optional]
         Identify gaps in existing research
         Generate copy-paste prompts for Microsoft Copilot for M365
         Run them externally, save results back into research/, then re-index
         ↓
Stage 3: Summarize Research
         Per-document TL;DRs compiled into working-files/research-summaries.md
         Answers: what does each individual file say?
         ↓
Stage 4: Synthesize
         One comprehensive unified narrative saved to output/
         Answers: what does everything together mean?
         ↓
Stage 5: Write Output
         Final deliverable in your chosen format
         (email, deck, exec summary, markdown doc, Word outline, bullet brief, Excel prompt)
```

Each stage requires your confirmation before advancing. You can stop at any point and
resume later by telling the assistant which stage you're picking up from.

---

## Chat Modes

Chat modes are selected from the **mode picker** in the Copilot Chat panel (the dropdown
at the top of the chat window). Each mode is a specialized operating context with its own
behavior, clarification protocol, and output rules.

**All modes:**

- Use **gpt-5.4** (latest model)
- Ask clarifying questions before acting — numbered (Q1, Q2...) with lettered options
  (A, B, C...). The recommended choice is always labeled `(Recommended)`.
- Enforce the `current-project/` scope rule
- Update `session-log.md` after completing tasks

---

### Workflow Mode

**Description:** Guided end-to-end walkthrough of all five stages.

**Best for:** Starting a new project, or wanting the assistant to handle the full
research-to-output pipeline without you having to coordinate between modes manually.

**How to use:**

1. Select **Workflow** from the mode picker
2. Tell the assistant where you want to start (new project, or resume at a stage)
3. Follow the guided prompts through each stage — the assistant confirms before advancing

**What happens at each stage:**

| Stage | What the assistant does |
|-------|------------------------|
| 1 — Index | Scans `research/`, builds `research-index.md`, reports file count and topics |
| 2 — Suggest Prompts | Identifies research gaps, generates up to 5 M365 Copilot prompts labeled [Work Mode] or [Web Mode] |
| 3 — Summarize | Produces per-document TL;DR + 3–5 bullets for every file, compiled into `research-summaries.md` |
| 4 — Synthesize | Reads all files, writes one unified narrative saved to `output/` |
| 5 — Write Output | Asks which format you need, produces the deliverable, saves to `output/`, offers revision |

**Example:**
```
You:       start
Assistant: Where would you like to begin?
           A) Stage 1 — new project (Recommended)
           B) Stage 2 — I already have research files
           C) Stage 3 — I have research files, skip to Summarize
           D) Stage 4 — I have summaries, start at Synthesize
           E) Stage 5 — I have a synthesis doc, just produce output

You:       A
Assistant: Found 6 files in current-project/research/. Building index...
           Index complete. Topics covered: competitive landscape, pricing,
           customer research, market sizing, regulatory overview, tech trends.
           Ready to move to Stage 2 (Suggest Prompts), or add more files first?
```

---

### Summarize Mode

**Description:** Distill research files into clear, concise per-document TL;DRs.

**Best for:** Getting a quick map of what each of your research files actually contains.
Use this before Synthesize when you want to review the material at a high level first.

**Key distinction from Synthesize:**
- **Summarize** = short TL;DR per individual document (what does *this file* say?)
- **Synthesize** = one unified narrative across all documents (what does *everything together* mean?)

**How to use:**

1. Select **Summarize** from the mode picker, or type `/summarize [topic or "all"]`
2. The assistant asks what to summarize:
   - A) All research files — TL;DR for every document *(Recommended)*
   - B) A specific file — load and summarize one file
   - C) A specific topic — find relevant files and summarize across them

**Output structure (per document):**
```
### filename.md
**TL;DR:** [1–2 sentences]

**Key Points:**
- [bullet]
- [bullet]
- ...

**Detail:** [organized by theme if multi-file]

**Gaps / Open Questions:** [what the file does NOT cover]
```

**Where it saves:** `current-project/working-files/research-summaries.md`

**Examples:**
```
/summarize all
/summarize competitive landscape
/summarize "competitor-analysis.md"
```

---

### Synthesize Mode

**Description:** Pull all collected research into one comprehensive, unified narrative.

**Best for:** After you've finished collecting research and want one authoritative document
that integrates everything. This is the definitive "what do we know" document — the
foundation for any downstream deliverable.

**Key distinction from Summarize:**
- **Summarize** = what does each individual file say?
- **Synthesize** = what does everything together mean? Written as a flowing narrative,
  not a list of per-file summaries.

**How to use:**

1. Select **Synthesize** from the mode picker, or type `/synthesize`
2. The assistant asks for audience and focus:
   - Q1: Who is the intended audience? (Internal leadership, external stakeholders, personal reference...)
   - Q2: Cover all themes equally, or focus on a specific angle?
3. The assistant states which files it will read, then reads all of them
4. Produces the synthesis document and saves to `output/`

**Synthesis document structure:**
```markdown
# [Topic] — Comprehensive Research Synthesis
**Date:** YYYY-MM-DD
**Sources:** [N] research files reviewed
**Prepared for:** [audience]

## Executive Overview
[3–5 sentences: the single most important thing the research collectively tells us]

## Background and Context
[What situation or problem does this research address?]

## Key Themes and Findings
### [Theme 1]
[Narrative integrating findings from all relevant sources]
### [Theme 2]
...

## Points of Tension or Contradiction
[Where do sources disagree or present conflicting information?]

## What the Research Does Not Cover
[Explicit gaps — questions left unanswered]

## Conclusions
[Direct, specific takeaways]

## Recommended Next Steps
[What actions or additional research would build on this?]
```

**Where it saves:** `current-project/output/YYYY-MM-DD-synthesis-[topic-slug].md`

---

### Draft Output Mode

**Description:** Produce a specific formatted deliverable from your research.

**Best for:** When you know what format you need and want to go straight to producing it.
Supports all seven output types (see [Output Types](#output-types) below).

**How to use:**

1. Select **Draft Output** from the mode picker, or type `/draft [type] [topic]`
2. The assistant confirms output type, topic, audience, and tone
3. Scans the research index, loads relevant files
4. Produces the deliverable following strict format standards
5. Saves to `output/`, confirms the filename, and offers a revision pass

**Format options:**

| # | Format | Use for |
|---|--------|---------|
| 1 | Email Draft | Stakeholder communications, updates, asks |
| 2 | Deck Slide Content | PowerPoint / Google Slides (maps 1:1 to slides) |
| 3 | Executive Summary | Senior audience, ~400 words max |
| 4 | Markdown Document | Shareable docs (Confluence, Notion, etc.) |
| 5 | Word Document Outline | Structured outline to finish in Word |
| 6 | Bullet Point Brief | Quick-consumption brief, 5–10 bullets |
| 7 | Excel Agent Prompt | Copy-paste prompt for Excel agent mode |

**Examples:**
```
/draft email stakeholder update on Q2 research
/draft exec-summary competitive landscape
/draft slide-content strategy overview
/draft bullet-brief key findings
/draft markdown-doc market analysis
/draft word-outline product strategy
/draft excel-prompt project tracker
```

---

### Write Mode

**Description:** Produce polished, well-structured written content across all output formats.

**Best for:** When you want fully authored prose rather than an outline or brief. Supports
the same seven output formats as Draft Output, plus general written content.

**How to use:**

1. Select **Write** from the mode picker
2. Specify the topic, format, audience, and tone
3. The assistant loads relevant research and applies the writing style guidelines

**Writing standards enforced:**
- Lead with the most important point — never bury the conclusion
- Active voice, short sentences, no filler words
- No corporate buzzwords (leverage, synergy, circle back, move the needle, robust, etc.)
- Conclusion first, then supporting detail
- One clear idea per paragraph

---

### Deep Research Mode

**Description:** Thorough, multi-file research analysis with structured findings and notes.

**Best for:** When you need to go deep on a specific question across all your research
files — not just a surface summary, but a rigorous analysis that identifies patterns,
contradictions, and gaps.

**How to use:**

1. Select **Deep Research** from the mode picker, or type `/research [topic]`
2. The assistant asks clarifying questions about scope and depth
3. States which files it will read and in what order
4. Reads each file fully, takes notes in `research-notes.md` as it goes
5. Produces a structured Research Report saved to `output/`

**Research Report structure:**
```markdown
## Research Question
[The specific question being investigated]

## Files Reviewed
[List of all files read]

## Key Findings
### [Theme 1]
[Findings organized by theme, synthesized across sources]
### [Theme 2]
...

## Contradictions or Tensions Found
[Where sources disagree]

## Gaps in the Research
[What the files don't cover]

## Conclusions
[Direct answers to the research question]

## Recommended Next Steps
[Follow-up research or actions]
```

**Where it saves:** `current-project/output/YYYY-MM-DD-research-report-[topic-slug].md`

**What makes it different from Synthesize:** Deep Research is focused on a specific
question and produces a structured report. Synthesize produces a comprehensive narrative
covering everything the research says, without a specific question framing.

---

### Suggest Prompts Mode

**Description:** Generate up to 5 ready-to-paste Microsoft Copilot for M365 prompts
based on your research — or starter prompts if you haven't collected any yet.

**Best for:** Identifying gaps in your existing research and generating targeted prompts
to run in Enterprise Copilot to fill those gaps. Also useful at the start of a project
when you haven't collected any research yet and need a starting point.

**How to use:**

1. Select **Suggest Prompts** from the mode picker, or type `/suggest-prompts`
2. If research files exist: the assistant reads the index, identifies gaps, generates
   targeted prompts
3. If no research files exist: asks your topic, generates 5 starter prompts

**About Microsoft Copilot modes:**

Each generated prompt is labeled with the appropriate mode for
[copilot.microsoft.com](https://copilot.microsoft.com):

- **[Work Mode]** — searches your organizational content: documents, emails, Teams
  messages, SharePoint, and calendar. Use for internal knowledge.
- **[Web Mode]** — searches the public web. Use for external research, market data,
  news, or public information.

**Output format:**
```markdown
## Suggested Microsoft Copilot Prompts

**Research context:** [1-sentence summary of what existing research covers]

**Identified gaps:**
- [gap 1]
- [gap 2]
- ...

---

**1. [Work Mode]**
> [Complete, copy-paste-ready prompt]
*Surfaces: [what this prompt is designed to find]*

**2. [Web Mode]**
> [Complete, copy-paste-ready prompt]
*Surfaces: [what this prompt is designed to find]*

[Up to 5 prompts total]
```

**Important:** This mode does NOT save output to `output/`. The prompts are for
manual copy-paste use in Enterprise Copilot. Save the results you get from Copilot
back into `current-project/research/` as `.md` or `.txt` files, then run `/reindex`.

**Prompt quality standards:**
- Each prompt is specific enough to return focused results
- Work Mode prompts reference organizational context ("in our recent emails", "from our team's documents")
- Web Mode prompts specify recency, geography, or industry when relevant
- No vague prompts like "tell me about X"

---

### Plan Mode

**Description:** Build structured, actionable plans from your research and goals.

**Best for:** Translating research findings into an execution plan — product launches,
project roadmaps, strategic initiatives, or any goal that requires phased execution.

**How to use:**

1. Select **Plan** from the mode picker, or type `/plan [goal]`
2. The assistant asks clarifying questions about the goal, desired outcome, and constraints
3. Scans the index, loads relevant research files
4. Produces a structured plan with phases, steps, risks, and success criteria
5. Offers to export the plan as a Markdown doc to `output/`

**Plan structure:**
```markdown
## Goal Statement
[Clear statement of what success looks like]

## Phases
### Phase 1: [Name]
- **Objective:** [what this phase achieves]
- **Key steps:** [bulleted list]
- **Dependencies:** [what must be true before this phase starts]
- **Timeline estimate:** [rough duration]

### Phase 2: ...

## Risks & Mitigations
| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| ...  | ...        | ...    | ...        |

## Success Criteria
[How you'll know the goal was achieved]

## Next Immediate Action
[The single next thing to do to move forward]
```

**Where it saves:** `current-project/output/YYYY-MM-DD-plan-[goal-slug].md`

---

### Brainstorm Mode

**Description:** Open ideation and creative exploration on any topic.

**Best for:** Exploring angles before committing to a direction, generating options
for a decision, or getting unstuck when you need fresh thinking. Uses your research
as a foundation but not a constraint.

**How to use:**

1. Select **Brainstorm** from the mode picker, or type `/brainstorm [topic]`
2. The assistant confirms the topic and desired creative direction
3. Checks the research index for relevant files to use as a springboard
4. Generates a diverse range of ideas: conventional, unconventional, and contrarian
5. Organizes ideas into clusters
6. Ends with 3 "provocative questions" to push thinking further
7. Offers to narrow down, prioritize, or hand off to Plan mode

**Output style:**

- Bold category headers for idea clusters
- 1–2 sentences per idea
- Ideas are not evaluated or filtered — volume and variety first
- 3 provocative questions at the end to challenge assumptions

**Important:** Brainstorm mode does not save output automatically. After reviewing
the ideas, you can ask the assistant to narrow down, prioritize, or hand off to
Plan mode to turn selected ideas into an actionable plan.

**Example:**
```
/brainstorm go-to-market approaches for a new enterprise product
```

---

### Review Mode

**Description:** Critically review and improve documents, arguments, or plans.

**Best for:** Getting structured, constructive feedback on any document before sharing
it — output you've produced in this system, a draft you wrote yourself, or a plan you
want pressure-tested.

**How to use:**

1. Select **Review** from the mode picker, or type `/review [file or topic]`
2. The assistant asks what to review and what criteria to focus on
3. Reads the full document before commenting (never comments on partial reads)
4. Cross-references against relevant research files if applicable
5. Structures feedback as: problem + solution (not just a list of complaints)
6. Rates the document on three dimensions

**Review output structure:**
```markdown
## Overall Assessment
[2–3 sentences on the document's overall quality and fit for purpose]

## Strengths
[What works well — be specific]

## Issues
### Critical
[Issues that significantly undermine the document's purpose]
### Important
[Issues that should be addressed before sharing]
### Minor
[Polish items — nice to fix but not blocking]

## Suggested Revisions
[Specific, actionable rewrites or restructuring suggestions]

## Quality Scores
Clarity [x/5] | Accuracy [x/5] | Completeness [x/5]
```

**Examples:**
```
/review synthesis-market-trends.md
/review my executive summary
/review the product launch plan
```

---

## Slash Commands

Slash commands are typed directly in the Copilot Chat input. They trigger the
corresponding mode with any parameters you provide passed in automatically.

| Command | What it does |
|---------|-------------|
| `/reindex` | Rebuild the research index from scratch — scans all files in `research/` and overwrites `research-index.md` |
| `/research [topic]` | Deep Research mode — thorough multi-file analysis on a specific topic |
| `/summarize [topic or "all"]` | Summarize mode — per-document TL;DRs for all files, a specific file, or a topic |
| `/synthesize` | Synthesize mode — one comprehensive unified narrative across all research |
| `/draft [type] [topic]` | Draft Output mode — produce a formatted deliverable |
| `/plan [goal]` | Plan mode — build a structured, actionable plan |
| `/brainstorm [topic]` | Brainstorm mode — open ideation session |
| `/review [file or topic]` | Review mode — critique and improve a document |
| `/suggest-prompts` | Suggest Prompts mode — generate M365 Copilot prompts based on research gaps |

### `/reindex` in detail

Run `/reindex` any time you add, remove, or significantly change files in
`current-project/research/`. The assistant will:

1. Delete existing `research-index.md` content
2. Re-scan all `.md` and `.txt` files in `current-project/research/`
3. Rebuild the index from scratch
4. Confirm the file count and that the index is ready

### `/draft` syntax examples

```
/draft email Q2 results update for leadership
/draft exec-summary competitive landscape analysis
/draft slide-content product strategy for all-hands
/draft bullet-brief key findings from customer research
/draft markdown-doc market sizing analysis
/draft word-outline go-to-market plan
/draft excel-prompt budget tracker with quarterly forecasts
```

---

## Output Types

All outputs save to `current-project/output/` using the naming convention:
`YYYY-MM-DD-[output-type]-[short-topic-slug].md`

---

### Email Draft

**Use for:** Stakeholder updates, meeting requests, decision asks, status reports

**Format rules:**
- Subject line at top, in bold
- Greeting, body paragraphs, closing
- First sentence = the so-what (main point, ask, or update)
- Short paragraphs or bullets — no walls of text
- Details go below the main point, not before it
- Minimal greeting and sign-off
- One clear ask per email
- Max ~300 words (unless topic requires more)

**Example filename:** `2026-03-26-email-draft-q2-stakeholder-update.md`

**Example structure:**
```markdown
**Subject: Q2 Research Summary — Decision Needed by Friday**

[First name],

We need a decision on the pricing strategy by Friday. Research from three
sources points to the same conclusion: the $299 tier is leaving money on the table.

Key findings:
- Competitor average is $349 for equivalent features
- 68% of survey respondents said price was "not a primary concern"
- Enterprise segment shows highest willingness-to-pay at $399+

Recommend: raise the SMB tier to $329 effective Q3. Happy to walk through
the full analysis.

Thanks,
[Name]
```

---

### Deck Slide Content

**Use for:** PowerPoint, Google Slides, Keynote presentations

**Format rules:**
- One H2 heading per slide
- 3–5 bullet points per slide, max 12 words each
- Optional "Speaker Notes:" section after each slide (in italics)
- Maps 1:1 into a presentation structure
- Lead each bullet with the insight or implication, not the data or activity

**Example filename:** `2026-03-26-slide-content-q2-strategy.md`

**Example structure:**
```markdown
## Market Opportunity

- SMB segment growing 22% YoY — fastest in 5 years
- Competitor pricing 15% above ours with lower feature parity
- Enterprise pipeline up 3x since product refresh

*Speaker Notes: Emphasize the pricing gap — this is the key message for the board.*

## Recommended Pricing Changes

- Raise SMB tier from $299 to $329 (10% increase)
- Introduce enterprise tier at $599 with SLA guarantee
- Phase implementation over Q3 to minimize churn risk
```

---

### Executive Summary

**Use for:** Senior leadership, boards, investors, busy stakeholders

**Format rules:**
- Max 1 page (~400 words)
- Four sections: Situation, Key Findings, Implications, Recommended Actions
- Written for a senior audience — no jargon, no excessive detail
- Conclusion-first structure in each section
- Descriptive section headers, not generic ones

**Example filename:** `2026-03-26-exec-summary-market-analysis.md`

**Example structure:**
```markdown
# Market Analysis — Executive Summary
**Date:** 2026-03-26

## Situation
[What problem or decision does this address? 2–3 sentences]

## Key Findings
- [Most important finding]
- [Second finding]
- [Third finding]

## Implications
[What do these findings mean for the business? 2–3 sentences]

## Recommended Actions
1. [Action 1 with owner and timeline]
2. [Action 2 with owner and timeline]
3. [Action 3 with owner and timeline]
```

---

### Markdown Document

**Use for:** Sharepoint, Confluence, Notion, GitHub, internal wikis

**Format rules:**
- H1 title, date, and author line at top
- Clear H2/H3 section structure
- Summary paragraph before body
- Peer-ready — suitable for direct sharing with colleagues

**Example filename:** `2026-03-26-markdown-doc-competitive-analysis.md`

---

### Word Document Outline

**Use for:** Longer documents you plan to author in Microsoft Word

**Format rules:**
- H1 document title
- H2 major sections with a 1–2 sentence description of what each section should contain
- H3 subsections as needed
- Written as a structural outline — you author the final prose in Word
- Includes a suggested page length note per major section

**Example filename:** `2026-03-26-word-outline-go-to-market-plan.md`

---

### Bullet Point Brief

**Use for:** Quick-consumption briefs for busy readers, pre-meeting prep notes

**Format rules:**
- Title line at top
- Optional one-sentence context header
- 5–10 tight bullets, max 20 words each
- Designed for speed — reader gets the full picture in under 60 seconds

**Example filename:** `2026-03-26-bullet-brief-customer-research-findings.md`

---

### Excel Agent Prompt

**Use for:** Generating a complete prompt to paste into Microsoft Excel's agent mode
to create a spreadsheet, tracker, or data model

**Format rules:**
- Labeled at top: `[Excel Agent Mode Prompt — paste directly into Excel Copilot]`
- One continuous paragraph or structured instruction block — no markdown headers
- Specifies: what data to include, how to structure columns/rows, any formulas or
  calculations needed, and the output goal
- Self-contained — the Excel agent can act without follow-up questions

**Example filename:** `2026-03-26-excel-prompt-project-budget-tracker.md`

---

## Research Index

The research index is the backbone of the system. It is a single file at
`current-project/working-files/research-index.md` that maps all research files so the
assistant can quickly determine which files are relevant to any task without loading
everything into context at once.

**Each entry includes:**

```markdown
### current-project/research/competitive-landscape.md
- **Type:** .md
- **Topic:** Competitive Landscape Analysis
- **Summary:** Covers the top 5 competitors in the deposits space, their product
  offerings, digital capabilities, and pricing structures as of Q1 2025.
- **Tags:** competitors, deposits, digital banking, pricing, market share
- **Last indexed:** 2026-03-26
```

**When to run `/reindex`:**

- After adding new files to `current-project/research/`
- After deleting or significantly updating existing research files
- If the assistant says the index is stale or missing
- At the start of a new session if you haven't indexed recently

**How the index is used during tasks:**

1. Assistant reads `research-index.md` first
2. Identifies relevant files by tags and summaries
3. Loads only those files into context
4. States to you which files it's using and why

This selective loading keeps tasks fast and focused — the assistant never reads files
that aren't relevant to the current task.

---

## Knowledge Boundaries

The system has strict rules about where information comes from.

**Primary source:** Files in `current-project/research/` are always prioritized.
The assistant will not substitute general knowledge when research files cover the topic.

**When general knowledge supplements research:**

If the research folder doesn't have enough information to fully address a task, the
assistant may supplement with general knowledge — but it will always flag it:

```
The average industry NPS for retail banks is approximately 30–35.
[General Knowledge — not sourced from research folder]
```

**What the assistant will never do:**

- Present general knowledge as if it came from your research files
- Fabricate research file content
- Blend sources without distinguishing them when you've asked for attribution

**Source attribution:**

By default, outputs do not include citations. If you need to know which files
were referenced, ask for it and the assistant will add a "## Sources Used" section
listing all files referenced and any `[General Knowledge]` supplements.

---

## Writing Style Standards

All outputs follow a consistent set of writing rules. These apply globally across
all output types.

### Global rules (all outputs)

- **Lead with the point.** The most important thing goes first — not third.
- **Active voice.** Avoid passive constructions unless there's a clear reason.
- **Short sentences.** No filler. If a word doesn't add meaning, cut it.
- **Conclusion first.** In any multi-paragraph output, state the conclusion before
  the supporting detail.
- **No corporate buzzwords.** Banned: leverage, synergy, circle back, move the
  needle, take this offline, deep dive (as a verb), robust, scalable (unless technical),
  impactful.
- **No throat-clearing.** Never open with: "It's worth noting that...", "Basically...",
  "In order to...", "As you can see..."
- **No hedging.** Cut: "it could be argued that", "in some ways", "sort of", "kind of".

### Slide bullets

- Lead with the insight or implication, not the data
- Max 12 words per bullet
- 3–5 bullets per slide
- No bullets starting with "We...", "The team...", "There is/are..."
- Speaker notes (if included) can be full sentences

### Email

- First sentence = the so-what
- Short paragraphs or bullets — no walls of text
- Details go below the main point
- Minimal greeting (first name or skip entirely)
- Minimal sign-off ("Thanks," or "Best,")
- One clear ask per email
- Max ~200 words for standard emails

### Formal documents (reports, memos, strategy docs)

- Conclusion-first structure — every section opens with its key finding
- Descriptive headers ("Revenue growth driven by SMB segment", not "Revenue Overview")
- One idea per paragraph (3–5 sentences max)
- Bullets for lists of 3 or more items
- No jargon without a brief parenthetical definition on first use
- Preferred structure: **Recommendation → Key Findings → Supporting Detail → Next Steps**

### General writing voice

- Mix short and medium sentences — avoid sentences over 25 words
- Plain English: "use" not "utilize", "show" not "demonstrate", "help" not "facilitate"
- Confident but not arrogant
- Specific over abstract — use numbers, names, and examples rather than generalities

**Override rule:** If you give explicit instructions about tone or style in your request,
those always take precedence over these defaults.

---

## Working Files Reference

The assistant automatically maintains these files in `current-project/working-files/`:

### `research-index.md`

A structured map of every file in `current-project/research/`. Created by the indexing
protocol, rebuilt by `/reindex`. The assistant reads this before every task to identify
which files are relevant.

### `research-notes.md`

Significant findings and observations recorded by the assistant during research tasks.
Updated by Deep Research mode and Synthesize mode as they read through files.

### `research-summaries.md`

Per-document TL;DRs for every file in `current-project/research/`. Created and
populated by Summarize mode (Stage 3 of the workflow). One entry per document with
TL;DR + key points.

### `session-log.md`

An audit trail of every completed task. The assistant appends an entry after each task:

```markdown
## 2026-03-26 Competitive Analysis Synthesis
- Mode: Synthesize
- Research files referenced: competitor-analysis.md, market-sizing.md, pricing-study.md
- Output produced: 2026-03-26-synthesis-competitive-landscape.md
- Notes: 3 files reviewed; identified pricing gap as primary theme
```

---

## File Naming Convention

All output files follow this convention:

```
YYYY-MM-DD-[output-type]-[short-topic-slug].md
```

**Output type tokens:**

| Output Type | Token |
|-------------|-------|
| Email Draft | `email-draft` |
| Deck Slide Content | `slide-content` |
| Executive Summary | `exec-summary` |
| Markdown Document | `markdown-doc` |
| Word Document Outline | `word-outline` |
| Bullet Point Brief | `bullet-brief` |
| Excel Agent Prompt | `excel-prompt` |
| Research Synthesis | `synthesis` |
| Deep Research Report | `research-report` |
| Plan | `plan` |

**Examples:**

```
2026-03-26-email-draft-q2-stakeholder-update.md
2026-03-26-exec-summary-market-analysis.md
2026-03-26-slide-content-q2-strategy.md
2026-03-26-synthesis-competitive-landscape.md
2026-03-26-research-report-customer-churn.md
2026-03-26-plan-product-launch.md
```

---

## Tips and Best Practices

**Start with good research files.** The quality of every output depends on what's in
`current-project/research/`. Well-structured `.md` files with clear headings give the
assistant better material to work with than unformatted `.txt` dumps.

**Run `/reindex` after adding files.** The assistant always reads the index first.
If you add a file without reindexing, the assistant won't know it exists.

**Use Summarize before Synthesize.** If you have more than a few files, running
Summarize first gives you a quick sanity check on what's actually in each file before
committing to a full synthesis.

**Use Suggest Prompts to find gaps early.** Running Stage 2 before summarizing can
save you from synthesizing incomplete research. The prompts it generates for Enterprise
Copilot can surface data points, internal documents, or external sources you didn't know existed.

**Tell the assistant your audience.** Synthesize, Draft Output, and Write modes all
ask about audience. The answer shapes vocabulary, detail level, and structure. "Internal
leadership" and "external stakeholders" will produce meaningfully different outputs from
the same research.

**Brainstorm before you plan.** If you're not sure which direction to go, run Brainstorm
first to generate options, then hand off to Plan mode with a chosen direction. This prevents
over-committing to a plan before you've fully explored the space.

**Use Review mode before sharing.** Run `/review` on any output before sending it.
The Clarity/Accuracy/Completeness scores and tiered issue list (Critical / Important / Minor)
give you a clear prioritized list of what to fix.

**Leverage session-log.md for handoffs.** If you're picking up a project that someone
else started (or one you haven't touched in a while), read `session-log.md` first.
It gives you a complete record of what was done, which files were used, and what was produced.

**One project at a time.** The system is scoped to `current-project/`. If you're switching
between projects, rename or archive the current `current-project/` folder and create a
fresh one for the new project. The `.copilotignore` and all instructions will apply to
whatever is in `current-project/` at the time.
