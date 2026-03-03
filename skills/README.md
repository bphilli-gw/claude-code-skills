# Skills

## What Are Skills?

Skills are instruction files that Claude Code loads automatically when they're relevant to your task. They live in `.claude/skills/` inside your project, each in its own folder with a `SKILL.md` file.

Think of a skill as a set of detailed instructions for a specific capability — like "how to safely read a long PDF" or "how to iteratively review and improve a draft."

## How to Install a Skill

Copy the skill folder into your project's `.claude/skills/` directory:

```bash
# From this repo:
cp -r skills/review-loop your-project/.claude/skills/

# Or tell Claude Code:
# "Copy the review-loop skill from [path-to-this-repo]/skills/review-loop/ into this project"
```

Your project should then look like:
```
your-project/
├── .claude/
│   └── skills/
│       └── review-loop/
│           └── SKILL.md
├── CLAUDE.md
└── ...
```

Claude will automatically use the skill when the situation calls for it.

## Available Skills

| Skill | What it does |
|-------|-------------|
| **[review-loop](review-loop/)** | Write-Review-Revise protocol. Forces iterative quality improvement with anti-rubber-stamp rules. Use this for any task that produces a document. |
| **[split-pdf](split-pdf/)** | Safe PDF reading. Splits long PDFs into 4-page chunks and reads them in batches. Prevents context window crashes and hallucination from large documents. |

## More Skills in Examples

The [examples/literature-tracker-skills/](../examples/literature-tracker-skills/) folder contains 12 additional skills from a production project. These are GiveWell-specific but useful as references for building your own skills. See the [ABOUT.md](../examples/literature-tracker-skills/ABOUT.md) for details.
