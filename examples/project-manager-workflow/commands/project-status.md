---
description: Check status of a project's configuration and recent syncs
argument-hint: <project-slug>
---

# Project Status Check

Display the current status of a project including configuration validity and recent sync history.

## Arguments

- **$ARGUMENTS**: Required project slug

## Your Task

### 1. Verify Project Exists

Check that `projects/$ARGUMENTS/` directory exists with required files:
- [ ] `config.yaml` - Project configuration
- [ ] `objectives.md` - Long-run objectives
- [ ] `memory/decisions-log.md` - Decisions log

### 2. Validate Configuration

Read `projects/$ARGUMENTS/config.yaml` and check:

**Required Fields:**
- [ ] `project.slug` matches directory name
- [ ] `project.name` is set
- [ ] At least one data source is configured
- [ ] At least one team member is listed

**Data Source Checks:**
- Slack: channels list not empty (if slack section exists)
- Gmail: labels or from_domains not empty (if gmail section exists)
- Meetings: local_folder or drive_folder_id set (if meetings section exists)
- Documents: at least one path or ID configured

### 3. Check Recent Syncs

Look for recent data in:
- `projects/$ARGUMENTS/raw/` - List last 3 sync dates
- `projects/$ARGUMENTS/summaries/` - List last 3 summary files
- `projects/$ARGUMENTS/overviews/` - List last 3 overview files

### 4. Generate Status Report

Output a status report:

```
=== Project Status: [Project Name] ===

Configuration: [VALID / ISSUES FOUND]
  - Slug: [slug]
  - Team Lead: [email]
  - Team Size: [N] members

Data Sources:
  - Slack: [Configured / Not configured]
    Channels: [list or "none"]
  - Gmail: [Configured / Not configured]
    Labels: [list or "none"]
  - Meetings: [Configured / Not configured]
    Location: [path or "none"]
  - Google Docs: [Configured / Not configured]
    Folders: [N] / Documents: [N]
  - Local Files: [Configured / Not configured]
    Paths: [N]

Recent Activity:
  - Last data pull: [DATE or "Never"]
  - Last summary: [DATE or "Never"]
  - Last overview: [DATE or "Never"]

Issues Found:
  - [Issue 1, if any]
  - [Issue 2, if any]

Recommendations:
  - [Recommendation based on issues]
```

### 5. Quick Actions

If issues found, suggest fixes:
- Missing config fields → "Edit projects/[slug]/config.yaml"
- No data sources → "Add at least one Slack channel or Gmail label"
- Never synced → "Run /weekly-sync [slug] to test"
- Stale data → "Last sync was [N] days ago, consider running /weekly-sync"

## Output

Display status report to user. No files are created or modified.
