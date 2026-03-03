---
description: Stage 4 - Update project memory with weekly summary
argument-hint: <project-slug>
---

# Stage 4: Project Memory Update

Append the weekly summary to the project's institutional memory, creating a running log of all decisions and activities.

## Arguments

- **$ARGUMENTS**: Required project slug

## Prerequisites

- Stage 1 synthesis complete
- Stage 2 overview generated
- Memory file exists or will be created: `projects/$ARGUMENTS/memory/decisions-log.md`

## Your Task

### 1. Create Memory Entry

Generate a condensed weekly summary designed for long-term reference:

```markdown
---

## Week of [WEEK_START] to [WEEK_END]

### Key Developments
- [Development 1]
- [Development 2]
- [Development 3]

### Decisions Made
- **[Decision Topic]**: [What was decided] *(Source: [type], [date])*
- **[Decision Topic]**: [What was decided] *(Source: [type], [date])*

### Action Items Assigned
- [Person]: [Task] (Due: [date if known])
- [Person]: [Task]

### Open Questions Carried Forward
- [Question] - Raised by [person], [date]

### Blockers/Risks Identified
- [Blocker/Risk]: [Status/mitigation]

### Notes
[Any other significant context worth preserving]

---
```

### 2. Append to Decisions Log

Read `projects/$ARGUMENTS/memory/decisions-log.md` and append the new entry at the TOP (most recent first).

If the file doesn't exist, create it with this header:

```markdown
# [Project Name] - Decisions Log

This document contains weekly summaries of project activities, decisions, and discussions. Most recent entries appear first.

---

[New weekly entry here]
```

### 3. Update Google Doc Memory Tab (Optional)

If the project config specifies a `memory_doc_id`:
- Use hardened-workspace MCP to update the document
- Append the weekly entry to the "Weekly Summaries" tab
- Maintain the same format as the local file

### 4. Prune Old Entries (Optional)

If the decisions log exceeds a reasonable size (e.g., 50 weeks), consider:
- Archiving older entries to `memory/archive/[YEAR]-decisions.md`
- Keeping the main log focused on recent months

## Memory Content Guidelines

### What to Include
- Decisions with clear outcomes
- Significant milestones reached
- Changes in direction or strategy
- Action items and who's responsible
- Blockers that affected progress
- Key external communications

### What to Exclude
- Routine status updates with no decisions
- Detailed task breakdowns (those live in to-dos)
- Full meeting transcripts (source data)
- Speculative discussions that led nowhere

### Writing Style
- Factual and concise
- Future-readable (someone in 6 months should understand)
- Include context for decisions ("We chose X because Y")
- Attribute decisions to people/meetings

## Output

- Primary: Updates `projects/$ARGUMENTS/memory/decisions-log.md`
- Optional: Updates Google Doc if configured

## Quality Checklist

- [ ] Weekly entry follows standard format
- [ ] Decisions clearly stated with rationale
- [ ] Entry prepended to log (most recent first)
- [ ] No sensitive information exposed
- [ ] Google Doc updated if configured
