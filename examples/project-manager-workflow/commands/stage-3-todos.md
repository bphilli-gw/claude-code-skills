---
description: Stage 3 - Extract and assign to-do items
argument-hint: <project-slug>
---

# Stage 3: To-Do Extraction

Extract action items from all sources, categorize them, and assign to team members.

## Arguments

- **$ARGUMENTS**: Required project slug

## Prerequisites

- Stage 1 synthesis available
- Team member list in `projects/$ARGUMENTS/config.yaml`

## Your Task

### 1. Scan for Action Items

Look for these signals in the raw and synthesized data:

**Explicit Action Items:**
- "Action item:", "TODO:", "AI:", "Next step:"
- "@mention with request"
- "Can you...", "Please...", "Would you..."
- "We need to...", "Someone should..."
- Meeting summary sections labeled "Action Items"

**Implicit Commitments:**
- "I'll...", "I will...", "I'm going to..."
- "Let's...", "We should..."
- "The plan is to..."
- "By [date], we'll have..."

**Decisions Requiring Follow-up:**
- "Once X happens, then..."
- "Pending Y, we'll..."
- "We're waiting on..."
- "After the meeting, [person] will..."

### 2. Categorize Each To-Do

For each identified item, determine:

**Urgency:**
| Level | Criteria |
|-------|----------|
| This Week | Explicit deadline this week, blocking others, marked urgent |
| Next 2 Weeks | Deadline in 1-2 weeks, important but not immediately blocking |
| This Month | Longer timeline, planning items, nice-to-haves |

**Importance:**
| Level | Criteria |
|-------|----------|
| Critical | Blocks major milestone, leadership attention, external deadline |
| High | Significant progress impact, multiple people waiting |
| Medium | Normal workflow item |
| Low | Enhancement, cleanup, can defer if needed |

**Type:**
- Task: Something to do/create/complete
- Decision: Something requiring a choice/approval
- Follow-up: Check on status, circle back
- Review: Read/comment/approve something

### 3. Assign to Team Members

Assignment logic (in order of preference):

1. **Explicit Assignment**: Source says "Alice will..." or "@alice please..."
2. **Role-Based**: Task matches someone's role (e.g., data analysis → Data Analyst)
3. **Context-Based**: Person was leading that discussion thread
4. **Unassigned**: Mark as "[Unassigned - needs discussion]" with suggested owner

Only assign to people listed in the project's `config.yaml` team section.

### 4. Generate To-Do Report

Save to `projects/$ARGUMENTS/summaries/[DATE]-todos.md`:

```markdown
# To-Do Extraction Report - [Project Name]
*Generated: [TIMESTAMP]*
*Data period: [START_DATE] to [END_DATE]*

## Summary
- Total items extracted: [N]
- By urgency: [X] this week, [Y] next 2 weeks, [Z] this month
- By importance: [A] critical, [B] high, [C] medium, [D] low
- Unassigned items: [N]

---

## To-Dos by Team Member

### [Team Member 1 Name] ([Role])

| Task | Urgency | Importance | Type | Source | Notes |
|------|---------|------------|------|--------|-------|
| [Clear, actionable description] | This Week | High | Task | Meeting 1/28 | [Context if helpful] |
| [Task 2] | Next 2 Weeks | Medium | Follow-up | Email from Bob | |

### [Team Member 2 Name] ([Role])

| Task | Urgency | Importance | Type | Source | Notes |
|------|---------|------------|------|--------|-------|
| [Task] | ... | ... | ... | ... | ... |

...

---

## Unassigned Items

| Task | Urgency | Importance | Source | Suggested Owner | Reason |
|------|---------|------------|--------|-----------------|--------|
| [Task] | This Week | High | Slack #channel | Alice (PI role) | Related to strategy |
| [Task] | Next 2 Weeks | Medium | Meeting | Bob (mentioned in discussion) | |

---

## Decisions Pending

| Decision | Context | Stakeholders | Deadline | Source |
|----------|---------|--------------|----------|--------|
| [What needs deciding] | [Brief background] | [Names] | [Date] | [Where raised] |

---

## Items Completed This Week

[If any tasks from previous weeks were completed, note them here]

- [Task] - Completed by [Name] on [Date]
```

## Output

- Primary: `projects/$ARGUMENTS/summaries/[DATE]-todos.md`
- The to-dos will also be incorporated into the Stage 2 overview

## Quality Checklist

- [ ] All sources scanned for action items
- [ ] Each to-do has urgency and importance
- [ ] Assignments match team roster
- [ ] Unassigned items have suggested owners
- [ ] Sources cited for each item
- [ ] Decisions pending section populated
