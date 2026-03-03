# Example: Grant Page Writer Workflow

## What This Is

A production Claude Code project that drafts GiveWell grant pages from Conditional Approvals (CAs) and other source documents. It follows a 6-stage pipeline from readiness assessment to final formatted output.

**Status**: Production. Used for real grant pages. Achieves ~40% time savings on drafting + vetting.

## Why It Works

1. **Multi-stage workflow with checkpoints**: Each stage produces a specific output and waits for user approval before continuing. This prevents Claude from going off-track on a 20-page document.

2. **Hard rules embedded in commands**: Every stage command includes explicit constraints (source discipline, numeric precision, sensitivity rules). These aren't suggested — they're mandatory. This is more reliable than putting rules in CLAUDE.md alone.

3. **Rich context folder**: The `context/` directory contains the GiveWell style guide, legibility guidance, a grant page template, and example grant pages. Claude reads these to calibrate its writing. The more examples you provide, the better the output.

4. **Sub-stage commands for the hardest part**: Stage 3 (drafting) has 6 sub-commands (3a-3f) that each handle one section. This keeps the context window focused and allows section-level feedback.

## Key Patterns to Reuse

- **Stage-gated workflow**: Break complex document production into stages with user checkpoints between each. See `commands/full-workflow.md` for how to orchestrate this.
- **Hard rules in every command**: Don't rely on Claude remembering rules from CLAUDE.md. Repeat critical constraints in each command file.
- **Context folder with calibration examples**: Give Claude 2-3 examples of "what good looks like" in a `context/` or `reference/` folder.
- **Download-doc command**: The `/download-doc` command pulls a Google Doc as markdown with comments preserved. Useful for any project that works with Google Docs.

## What's NOT Reusable

- The specific stage commands are tightly coupled to GiveWell's grant page format, CA structure, and publication standards.
- The sensitivity rules (what can/can't be in a public grant page) are GiveWell-specific.
- The template and examples reference GiveWell's specific document structure.

## Files in This Example

- `CLAUDE.md` — Project instructions showing the writing-workflow pattern
- `commands/full-workflow.md` — The orchestrator command
- `commands/stage-0-assess.md` through `stage-5-finalize.md` — Individual stage commands
- `commands/stage-3a-opening.md` through `stage-3f-closing.md` — Sub-stage drafting commands
- `commands/download-doc.md` — Google Doc download utility
