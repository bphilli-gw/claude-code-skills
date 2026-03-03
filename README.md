# GiveWell Claude Code Assets

Shared skills, templates, and reference documents for using Claude Code at GiveWell.

## Quick Start

```bash
# 1. Clone this repo (one-time)
git clone https://github.com/bphilli5/givewell-claude-code.git

# 2. Open your own project in Claude Code

# 3. Tell Claude:
#    "Copy the review-loop skill from ~/Documents/givewell-claude-code/skills/review-loop/ into this project's .claude/skills/ folder"
```

To get updates later: `cd givewell-claude-code && git pull`

---

## What's Here

### Getting Started (start here if you're new to Claude Code)

| File | What it is |
|------|-----------|
| [Getting started guide](getting-started/claude-code-getting-started-guide.md) | Setup instructions and tips for first use |
| [Things to try with AI](getting-started/things-to-try-with-ai.md) | 27 concrete tasks ordered from simple to complex |
| [Prompt library](getting-started/prompt-library.md) | Ready-to-use prompts organized by task type |

### Skills (copy into your project's `.claude/skills/`)

Skills are reusable instruction files that Claude loads automatically when relevant. Copy the whole folder into your project.

| Skill | What it does |
|-------|-------------|
| [review-loop](skills/review-loop/) | Write-Review-Revise protocol for iterative quality improvement. Forces Claude to re-read its own work, apply a checklist, and fix issues. Includes anti-rubber-stamp rules so Claude doesn't approve its own first draft. |
| [split-pdf](skills/split-pdf/) | Safe PDF reading in chunks. Splits long PDFs into 4-page pieces and reads 3 at a time to avoid context window issues. Prevents hallucination from skimming large documents. |

### CLAUDE.md Templates (copy and customize for your project)

Templates for the `CLAUDE.md` file that sits at the root of every Claude Code project. Pick the one closest to your use case and customize.

| Template | Use when... |
|----------|------------|
| [Simple project](claude-md-templates/simple-project.md) | Quick tasks, one-off analyses, small projects |
| [Research project](claude-md-templates/research-project.md) | Investigations, literature reviews, data analysis |
| [Writing workflow](claude-md-templates/writing-workflow.md) | Multi-stage document production (grant pages, reports, plans) |
| [Knowledge base](claude-md-templates/knowledge-base.md) | "Second brain" projects with accumulated context across sessions |

### Reference Documents (copy into your project folder)

GiveWell writing standards that any project producing written output should reference.

| Document | What it is |
|----------|-----------|
| [GiveWell style guide](reference/givewell-style-guide.md) | Required names, terms, citation style, and formatting conventions |
| [Legibility guidance](reference/legibility-guidance.md) | What makes GiveWell writing clear and contestable — examples of good and bad legibility |

### MCP Setup Guides (follow once per integration)

MCP (Model Context Protocol) lets Claude Code connect to external services. These are one-time setup guides.

| Guide | What it connects |
|-------|-----------------|
| [Google Workspace](mcp-setup/google-workspace.md) | Gmail, Google Drive, Docs, Calendar, Sheets |
| [Slack](mcp-setup/slack.md) | Channel reading, message search, posting |

### Examples (read for inspiration — don't copy directly)

Full production workflows with annotations explaining what works and why. These are reference material, not drop-in tools.

| Example | What it demonstrates |
|---------|---------------------|
| [Grant page workflow](examples/grant-page-workflow/) | 6-stage document production pipeline with hard rules and sub-stages |
| [Literature tracker skills](examples/literature-tracker-skills/) | Composable skills architecture — small skills orchestrated by commands |
| [Project manager workflow](examples/project-manager-workflow/) | Multi-source data aggregation from Slack, Gmail, and local files |

Start with each example's `ABOUT.md` for an overview of the patterns and what to reuse.

---

## How to Copy Assets Into Your Project

### Option 1: Tell Claude Code (recommended)

The easiest way. Open your project in Claude Code and say:

> "Copy the review-loop skill from `C:/Users/[your-username]/Documents/givewell-claude-code/skills/review-loop/` into this project's `.claude/skills/` folder"

Claude will read the file from the shared repo and create it in your project.

### Option 2: Copy manually

```bash
# Copy a skill
cp -r ~/Documents/givewell-claude-code/skills/review-loop your-project/.claude/skills/

# Copy a CLAUDE.md template
cp ~/Documents/givewell-claude-code/claude-md-templates/research-project.md your-project/CLAUDE.md
```

### Option 3: Browse on GitHub (no git needed)

1. Navigate to the file on [github.com/bphilli5/givewell-claude-code](https://github.com/bphilli5/givewell-claude-code)
2. Click the file, then click "Raw"
3. Select All, Copy, then paste into a new file in your project

---

## Recently Added

- **2026-03-03**: Initial release — 2 skills, 4 CLAUDE.md templates, reference docs, MCP setup guides, 3 annotated examples, getting started materials

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to add or update assets.

Questions? Reach out to Brendan or post in #ai-discussion.
