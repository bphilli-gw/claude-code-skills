---
description: Stage 0 - Gather raw data from all configured sources
argument-hint: <project-slug>
---

# Stage 0: Data Gathering

Pull raw data from all configured sources for the specified project.

## Arguments

- **$ARGUMENTS**: Required project slug (e.g., "malaria-vaccine-trial")

## Prerequisites

- Project configuration exists at `projects/$ARGUMENTS/config.yaml`
- MCP servers are configured and authenticated in `.mcp.json`

## Your Task

### 1. Load Project Configuration

Read `projects/$ARGUMENTS/config.yaml` to get:
- Asana project GIDs and filters
- Slack channels and keywords
- Gmail labels and filters
- Meeting transcript locations
- Google Docs folder/document IDs
- Local file paths and patterns

### 2. Create Output Directory

Create `projects/$ARGUMENTS/raw/[YYYY-MM-DD]/` for today's date.

### 3. Pull Asana Tasks

If `sources.asana.enabled` is true:
- Use the Asana MCP tools to search for tasks in the configured project(s)
- For each `project_gids` entry, pull tasks updated in the lookback period
- Include task name, assignee, status, due date, notes, and comments
- Filter by keywords if specified
- If `project_gids` is empty, list the user's workspaces and projects to help them configure

Save to `asana-tasks.json`:
```json
{
  "source": "asana",
  "pulled_at": "[ISO timestamp]",
  "date_range": {"start": "...", "end": "..."},
  "projects": [
    {
      "project_gid": "...",
      "project_name": "...",
      "tasks": [
        {
          "gid": "...",
          "name": "...",
          "assignee": "...",
          "status": "...",
          "due_date": "...",
          "notes": "...",
          "comments": [
            {"author": "...", "text": "...", "created_at": "..."}
          ],
          "modified_at": "..."
        }
      ]
    }
  ]
}
```

### 4. Pull Slack Messages

For each configured channel:
- Use Slack MCP to search messages from the past 7 days (or configured lookback)
- Include thread replies
- Filter by keywords if specified
- Save to `slack-messages.json`:
```json
{
  "source": "slack",
  "pulled_at": "[ISO timestamp]",
  "date_range": {"start": "...", "end": "..."},
  "channels": [
    {
      "channel": "#channel-name",
      "messages": [
        {"timestamp": "...", "user": "...", "text": "...", "thread_replies": [...]}
      ]
    }
  ]
}
```

### 5. Pull Emails

For Gmail, search by:
- Labels (e.g., "Projects/Example")
- From domains (e.g., "@partner.org")
- Subject keywords

Extract and save to `emails.json`:
```json
{
  "source": "gmail",
  "pulled_at": "[ISO timestamp]",
  "date_range": {"start": "...", "end": "..."},
  "emails": [
    {"date": "...", "from": "...", "subject": "...", "body_preview": "...", "labels": [...]}
  ]
}
```

### 6. Pull Meeting Transcripts

For local folder or Google Drive:
- List files matching patterns (*.txt, *.md, *.docx)
- Filter to files modified in lookback period
- Read content of each file

Save to `meetings.json`:
```json
{
  "source": "meetings",
  "pulled_at": "[ISO timestamp]",
  "transcripts": [
    {"filename": "...", "date": "...", "content": "..."}
  ]
}
```

### 7. Pull Google Docs

For each configured folder/document:
- Get document content
- Note recent edits/comments if available

Save to `documents-gdocs.json`:
```json
{
  "source": "google_docs",
  "pulled_at": "[ISO timestamp]",
  "documents": [
    {"title": "...", "doc_id": "...", "content": "...", "last_modified": "..."}
  ]
}
```

### 8. Pull Local Files

For each configured path:
- Glob for matching files
- Filter to recently modified
- Read content

Save to `documents-local.json`:
```json
{
  "source": "local_files",
  "pulled_at": "[ISO timestamp]",
  "files": [
    {"path": "...", "filename": "...", "content": "...", "modified": "..."}
  ]
}
```

## Output Checklist

After completion, verify:
- [ ] `projects/$ARGUMENTS/raw/[DATE]/` directory created
- [ ] Each source attempted (log errors for unavailable sources)
- [ ] JSON files created for each data type
- [ ] Date range correctly applied

## Error Handling

- If Asana MCP unavailable: Log error, continue with other sources
- If Slack MCP unavailable: Log error, continue with other sources
- If Gmail MCP unavailable: Log error, continue with other sources
- If a file can't be read: Log and skip, continue with others
- Always produce output files even if partially populated
