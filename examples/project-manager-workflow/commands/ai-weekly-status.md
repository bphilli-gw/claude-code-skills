---
description: Generate weekly AI projects status check-in
argument-hint: [lookback-days] (default: 7)
---

# AI Projects Weekly Status

Generate a legible check-in on AI projects by gathering data from Google Drive, Gmail, and local files, then producing a structured status overview.

## Arguments

- **$ARGUMENTS**: Optional number of days to look back (default: 7)

## Workflow

### 1. Get Current Date and Lookback Period

Use `mcp__hardened-workspace__time_getCurrentDate` to get today's date. Calculate the lookback start date based on $ARGUMENTS or default to 7 days.

### 2. Search Google Drive for AI Documents

Search Drive for recently modified AI-related documents:

```
Query: "AI" modified after [lookback-start-date]
```

Key documents to look for:
- AI projects planner (spreadsheet) - for project tracking
- AI Success Stories - for wins/progress
- AI Quick Start Guide - for documentation updates
- AI Shadowing notes & potential projects - for new project ideas
- AI hackathon plan - for event planning
- State of AI at GiveWell - for strategic context

For each relevant document found:
- Note the title, last modified date, and who modified it
- For spreadsheets (AI projects planner), read the content to get project status
- For docs, read key sections if recently modified

### 3. Search Gmail for AI-Related Emails

Search Gmail for recent AI-related emails:

```
Query: subject:(AI OR "artificial intelligence" OR LLM OR Claude OR GPT) newer_than:[lookback]d
```

Also search for emails from/to key collaborators on AI work.

For each relevant email:
- Note sender, date, subject, and brief snippet
- Flag any action items or decisions mentioned

### 4. Read Local AI Planning Files

Check the local AI-planning directory for updates:
- `C:/Users/Brendan Phillips/Documents/AI-planning/`
- Meeting notes, knowledge base docs

### 5. Read Current Project Memory

Read existing status files:
- `projects/ai-planning/memory/decisions-log.md` - for recent decisions
- `projects/ai-planning/overviews/` - most recent overview for context

### 6. Generate Status Check-In

Create a legible check-in following GiveWell standards. Write to `projects/ai-planning/overviews/[YYYY-WW]-status.md`:

```markdown
# AI Projects Status Check-In
**Week of [DATE]** | Generated [TIMESTAMP]

## Bottom Line

[1-2 sentence summary of overall AI work status this week]

## What's Happened This Week

### Key Activities
- [Activity 1 with source reference]
- [Activity 2 with source reference]

### Documents Updated
| Document | Last Modified | Key Changes |
|----------|---------------|-------------|
| [Doc name] | [Date] | [Brief description] |

### Emails/Communications
- [Notable email threads or decisions]

## Project Status

[For each active project from AI projects planner:]

### [Project Name]
- **Status**: [Active/Paused/Completed/Blocked]
- **Recent Progress**: [What happened]
- **Current Blocker**: [If any]
- **Next Step**: [Specific action]

## Key Uncertainties

- [Uncertainty 1 - what you're unsure about and what would resolve it]
- [Uncertainty 2]

## Next Steps (Next 1-2 Weeks)

| Action | Owner | Priority | Notes |
|--------|-------|----------|-------|
| [Action item] | [Person] | High/Med/Low | [Context] |

## Decisions Needed

- [Any decisions that need manager input]

---
*Sources: [List of documents, emails, and files consulted]*
```

### 7. Update Decisions Log

If any decisions were made or significant events occurred, append to `projects/ai-planning/memory/decisions-log.md`:

```markdown
## Week of [DATE]

### Decisions Made
- [Decision with context]

### Key Events
- [Event with source]
```

### 8. Present Summary to User

After generating the files, present a brief verbal summary:
- Overall status (1 sentence)
- Top 2-3 highlights
- Any items needing attention
- Link to generated status file

## Output Files

- `projects/ai-planning/overviews/[YYYY-WW]-status.md` - Full status check-in
- `projects/ai-planning/memory/decisions-log.md` - Updated with new entries (if any)

## Key Google Drive Documents (Reference)

These are known AI-related docs to check:
- `1n8w3gJHGhD58kQAiFqZHq7PatKUImGy5AsyaT6KmqD0` - AI projects planner (spreadsheet)
- `1UreciwXpQPCcJnRO3Pws7YKM9hJ8f6ZNmpmzGue4Qxs` - AI Success Stories
- `1R589GtPZu-ACmyfWuQnviWSKhovcn2FyiZmv4rT3JP8` - AI Quick Start Guide
- `1w3NnA21pOrJ_SZ9d02G-RD1IgfI4JBvZy7vNmm4lE0Y` - AI Shadowing notes
- `1cUFf9H-oQL9O7CtiUG-lwzE85rz1MbEBSI0ceCY-y5I` - AI hackathon plan
- `1vr58vurD6lc3Gw7Y-MqZYLOYGVfEUlNkApzQDRtoJNc` - State of AI at GiveWell

## Legibility Standards

Follow GiveWell check-in format:
1. **Bottom line first** - What would you do/conclude if you stopped now?
2. **Be specific** - Use concrete examples, dates, names
3. **Quantify uncertainty** - What are you unsure about? What would change your mind?
4. **Actionable next steps** - Verb + object + owner
5. **Source everything** - Every claim traces to a document, email, or meeting
