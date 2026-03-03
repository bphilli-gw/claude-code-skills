---
description: Run full weekly project intelligence sync
argument-hint: [project-slug] (optional - run for all active projects if omitted)
---

# Weekly Project Intelligence Sync

This command orchestrates the full weekly workflow for generating project overviews and summaries.

## Arguments

- **$ARGUMENTS**: Optional project slug. If provided, run for that project only. If omitted, run for all active projects in `config/projects.yaml`.

## Workflow

Execute the following stages in sequence:

### 1. Load Configuration

Read `config/projects.yaml` to get the list of active projects. If a specific project slug was provided, filter to just that project.

### 2. For Each Project, Execute All Stages

For each project:

1. **Stage 0: Gather** - `/stage-0-gather [slug]`
   - Pull raw data from Slack, Gmail, Google Docs, meeting transcripts, local files
   - Save to `projects/[slug]/raw/[DATE]/`

2. **Stage 1: Synthesize** - `/stage-1-synthesize [slug]`
   - Deduplicate and thread related items
   - Extract entities (people, dates, decisions, actions)
   - Create unified activity log

3. **Stage 2: Overview** - `/stage-2-overview [slug]`
   - Generate 3-page project intelligence brief
   - Strategic overview, priorities, to-do lists

4. **Stage 3: To-Dos** - `/stage-3-todos [slug]`
   - Extract action items from all sources
   - Assign to team members
   - Categorize by urgency

5. **Stage 4: Memory** - `/stage-4-memory [slug]`
   - Append weekly summary to decisions log
   - Update project memory

6. **Stage 5: Calendar** - `/stage-5-calendar [slug]`
   - Create calendar events for to-dos
   - Post summary to Slack
   - Notify team members

### 3. Summary Report

After processing all projects, provide a summary:
- Projects processed: [count]
- Data sources accessed: [list]
- To-dos created: [count]
- Any errors or data gaps encountered

## Error Handling

- If a stage fails for one project, log the error and continue with other projects
- If a data source is unavailable, continue with available sources and note the gap
- Never let one project's failure block processing of others

## Example Usage

```bash
# Run for all active projects
/weekly-sync

# Run for a specific project
/weekly-sync malaria-vaccine-trial
```
