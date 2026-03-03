# Contributing to GiveWell Claude Code Assets

## How to Contribute

### If you're a vanguard member (non-technical)

1. **Share in #ai-discussion**: Post the skill, command, or prompt that worked well for you. Include the file content and a brief description of what it does.
2. **Send to Brendan**: Email or Slack Brendan with the file and context. He'll review, edit if needed, and add it to the repo.
3. **Suggest improvements**: If something in the repo doesn't work well, let Brendan know. Feedback is as valuable as new contributions.

### If you're comfortable with git

1. Clone the repo and create a branch
2. Add or modify your asset
3. Submit a pull request with a description of what you added/changed
4. Brendan will review and merge

## Standards for New Assets

### Skills (`.claude/skills/`)

- Each skill lives in its own folder with a `SKILL.md` file
- The skill must work without project-specific dependencies (no references to files that only exist in one project)
- Include a "When This Skill Applies" section at the top
- Include a "Quick Reference" table at the bottom

### Commands (`.claude/commands/`)

- Each command is a single `.md` file
- Include a comment at the top explaining what the command does and when to use it
- Commands should either be self-contained or reference only skills available in this repo

### CLAUDE.md Templates

- Use `[brackets]` for parts the user needs to customize
- Include inline comments explaining what each section is for
- Keep templates concise — they're starting points, not comprehensive guides

### Reference Documents

- Must be relevant to multiple projects (not just one)
- Include a "How to use this doc" section if the document isn't self-explanatory

## What NOT to Add

- Assets with hardcoded credentials, API keys, or OAuth secrets
- Files containing sensitive GiveWell internal information (staff evaluations, salary data, etc.)
- Large binary files (PDFs, images) — link to them instead
- Anything that only works in one specific project without modification

## Updating Existing Assets

When you update an asset:
1. Update the "Recently Added" section in README.md with the date and what changed
2. If the asset exists in a source project too (e.g., `review-loop` is also in `ai-literature-tracker`), note that the shared repo version may differ from the source

## Questions?

Ask Brendan or post in #ai-discussion.
