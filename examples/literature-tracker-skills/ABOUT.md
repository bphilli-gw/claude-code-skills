# Example: Literature Tracker — Composable Skills Architecture

## What This Is

A Claude Code project that produces Quick Evidence Assessments (QEAs), BOTECs, peer reviews, and research reports. Built on a **composable skills architecture** — small, reusable skills that are orchestrated by commands.

**Status**: Piloting with the water team. QEA outputs are promising; BOTEC research depth is hard to prompt for.

## Why It Works

1. **Skills are building blocks**: Instead of one giant prompt, each capability (search papers, read PDFs, write a BOTEC, review a BOTEC) is a separate skill file. Commands orchestrate these skills into workflows.

2. **Write-Review-Revise loop**: Every output goes through the `review-loop` skill — write a draft, switch to reviewer mode, apply a checklist, fix issues, repeat. Anti-rubber-stamp rules prevent Claude from approving its own first draft. This is the single most reusable pattern in the project.

3. **Separation of writer and reviewer skills**: Each document type has a paired writer skill (e.g., `botec-writer`) and reviewer skill (e.g., `botec-reviewer`). The reviewer has a different persona and checklist than the writer.

4. **Split-PDF for safe reading**: Academic papers are split into 4-page chunks and read in batches of 3 to avoid context window issues. This prevents the common failure mode of Claude hallucinating paper contents when the PDF is too large.

## Key Patterns to Reuse

- **Composable skills**: Build small skills, then orchestrate them with commands. Much easier to debug and improve than monolithic prompts.
- **Write-Review-Revise loop**: The `review-loop` skill (available in `skills/review-loop/` in the shared repo) works for any iterative drafting workflow.
- **Split-PDF**: The `split-pdf` skill (available in `skills/split-pdf/` in the shared repo) works for any project that reads long PDFs.
- **Anti-rubber-stamp rules**: Force at least 2 blocking issues on the first review iteration. This single rule dramatically improves output quality.

## What's NOT Reusable (without modification)

- The writer/reviewer skills reference GiveWell's specific cost-effectiveness framework, intervention reports, and QEA template.
- The `literature-search` skill calls project-specific Python modules for Semantic Scholar and PubMed.
- The `relevance-score` skill is specific to GiveWell's CEA-relevance scoring criteria.

## Files in This Example

- `skills/review-loop/SKILL.md` — The core write-review-revise protocol (also available as a standalone skill in the shared repo)
- `skills/split-pdf/SKILL.md` — Safe PDF reading protocol
- `skills/literature-search/SKILL.md` — Academic paper discovery
- `skills/botec-writer/SKILL.md` & `skills/botec-reviewer/SKILL.md` — Paired writer/reviewer for BOTECs
- `skills/qea-writer/SKILL.md` & `skills/qea-reviewer/SKILL.md` — Paired writer/reviewer for QEAs
- `skills/report-writer/SKILL.md` & `skills/report-reviewer/SKILL.md` — Research reports
- `skills/peer-review-writer/SKILL.md` & `skills/review-critic/SKILL.md` — Peer reviews
- `skills/relevance-score/SKILL.md` — Paper relevance scoring
