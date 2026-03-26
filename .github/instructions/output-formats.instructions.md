---
applyTo: "**"
---

# Output Format Standards

All outputs produced by the researcher must be saved to `current-project/output/`
with a descriptive, dated filename (e.g., `2025-06-01-email-draft-q2-update.md`).

## Supported Output Types

### Email Draft
- Subject line at top (bold)
- Greeting, body paragraphs, closing
- Professional tone unless user specifies otherwise
- Max 300 words unless user specifies longer

### Markdown Doc (Shareable / Peer-Ready)
- H1 title, date, and author line at top
- Clear H2/H3 section structure
- Summary paragraph before body
- Suitable for sharing directly with colleagues or pasting into Confluence/Notion

### Deck Slide Content (Markdown Formatted)
- One H2 per slide
- 3–5 bullet points per slide, max 12 words each
- Optional "Speaker Notes:" section after each slide in italics
- Designed to map 1:1 into a PowerPoint or Google Slides structure

### Executive Summary
- Max 1 page (approx. 400 words)
- Sections: Situation, Key Findings, Implications, Recommended Actions
- Written for a senior audience — no jargon, no excessive detail

### Bullet Point Brief
- Title line
- 5–10 tight bullets (max 20 words each)
- Optional one-sentence context header
- Designed for quick consumption

### Word Document Outline
- H1 document title
- H2 major sections with a 1–2 sentence description of what each section should contain
- H3 subsections as needed
- Written as a structural outline, not full prose — the user will author the final content in Word
- Include a suggested page length note per major section

### Excel Agent Prompt
- A complete, self-contained prompt the user can paste directly into Microsoft Excel's agent mode
- Must specify: what data to include, how to structure columns/rows, any formulas or calculations needed, and the output goal
- Format: one continuous paragraph or structured instruction block — no markdown headers
- Include enough context that the Excel agent can act without follow-up questions
- Label at top: `[Excel Agent Mode Prompt — paste directly into Excel Copilot]`

## File Naming Convention
`YYYY-MM-DD-[output-type]-[short-topic-slug].md`
Examples:
- `2025-06-01-email-draft-stakeholder-update.md`
- `2025-06-01-exec-summary-market-analysis.md`
- `2025-06-01-slide-content-q2-strategy.md`
