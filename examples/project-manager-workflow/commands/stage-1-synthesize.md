---
description: Stage 1 - Synthesize raw data into unified activity log
argument-hint: <project-slug>
---

# Stage 1: Data Synthesis

Process raw data from Stage 0 into a unified, deduplicated activity log.

## Arguments

- **$ARGUMENTS**: Required project slug

## Prerequisites

- Stage 0 completed: Raw data exists in `projects/$ARGUMENTS/raw/[DATE]/`

## Your Task

### 1. Load Raw Data

Read all JSON files from the most recent `projects/$ARGUMENTS/raw/[DATE]/` directory:
- `slack-messages.json`
- `emails.json`
- `meetings.json`
- `documents-gdocs.json`
- `documents-local.json`

### 2. Deduplication

The same information often appears in multiple sources. Identify and consolidate:
- Topics discussed in a meeting that were followed up via email
- Slack messages that reference email threads
- Document changes discussed in meetings

Create single entries with multiple source citations.

### 3. Chronological Threading

Group related items into "threads" showing how topics evolved:
- Link messages/emails about the same topic
- Connect meeting discussions to follow-up actions
- Show the progression of decisions over time

### 4. Entity Extraction

Extract and tag:
- **People**: Names mentioned, match to team roster where possible
- **Dates/Deadlines**: Any mentioned dates, deadlines, milestones
- **Decisions**: Explicit decisions made ("We decided to...", "Agreed that...")
- **Action Items**: Tasks assigned or committed to
- **Questions**: Open questions raised but not yet resolved
- **Blockers**: Issues preventing progress

### 5. Topic Clustering

Group items into logical categories:
- Progress updates
- Blockers/issues raised
- Decisions made
- Action items assigned
- Planning discussions
- External communications

### 6. Importance Signals

Flag items that are likely high-priority:
- Mentioned by team lead or PI
- Discussed multiple times across sources
- Have explicit deadlines
- Marked urgent in source
- Related to critical path activities

## Output Format

Save to `projects/$ARGUMENTS/summaries/[DATE]-synthesis.md`:

```markdown
# Activity Synthesis - [Project Name]
*Period: [START_DATE] to [END_DATE]*
*Generated: [TIMESTAMP]*

## Summary Statistics
- Slack messages processed: [N]
- Emails processed: [N]
- Meeting transcripts processed: [N]
- Documents reviewed: [N]
- Unique threads identified: [N]

---

## Thread 1: [Topic Name]
*Importance: High/Medium/Low*

**Timeline:**
- [DATE] Meeting: [Summary] *(Source: meeting transcript)*
- [DATE] Email: [Follow-up] *(Source: email from X)*
- [DATE] Slack: [Update] *(Source: #channel)*

**Key Points:**
- [Point 1]
- [Point 2]

**Decisions Made:**
- [Decision, if any]

**Action Items:**
- [Action with assignee if known]

**Open Questions:**
- [Question, if any]

---

## Thread 2: [Topic Name]
...

---

## Standalone Items

### Progress Updates
- [Update] *(Source: [type], [date])*

### Questions Raised (Unresolved)
- [Question] *(Asked by: X, Source: [type])*

### External Communications
- [Summary] *(Source: [type])*

---

## Extracted Entities

### People Mentioned
- [Name] - [Context/Role if known]

### Dates/Deadlines Referenced
- [Date]: [What's due/happening]

### Key Decisions
- [Decision] *(Made: [date], Source: [type])*

### Action Items (Raw)
- [Action] *(Assigned to: [name if known], Source: [type])*
```

## Quality Checklist

- [ ] All raw data files processed
- [ ] Duplicates consolidated with multiple source citations
- [ ] Items grouped into coherent threads
- [ ] Entities extracted and listed
- [ ] Importance signals noted
- [ ] Output saved to summaries directory
