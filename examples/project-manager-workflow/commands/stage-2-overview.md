---
description: Stage 2 - Generate 3-page project overview
argument-hint: <project-slug>
---

# Stage 2: Generate 3-Page Overview

Create the weekly project intelligence brief from synthesized data.

## Arguments

- **$ARGUMENTS**: Required project slug

## Prerequisites

- Stage 1 completed: Synthesis exists at `projects/$ARGUMENTS/summaries/[DATE]-synthesis.md`
- Objectives file exists: `projects/$ARGUMENTS/objectives.md`

## Your Task

Read the synthesis and objectives, then generate a 3-page overview.

### Page 1: Strategic Overview (~500 words)

```markdown
# [Project Name] - Weekly Intelligence Brief
*Week of [WEEK_START] to [WEEK_END]*
*Generated: [TIMESTAMP]*

---

## Strategic Objectives Reminder

[Pull 3-5 key objectives from objectives.md. These are the long-run goals that give context to weekly activities.]

- **Objective 1**: [Description]
- **Objective 2**: [Description]
- ...

## Current Strategic Position

[2-3 paragraphs synthesizing where the project stands relative to objectives. This is the "big picture" view. Draw from:
- Meeting discussions about strategy
- Email threads about direction
- Document changes reflecting progress or pivots]

## Key Developments This Week

[5-8 most significant developments, each with source reference]

- **[Topic]**: [What happened/changed] *(Source: [meeting/email/slack], [date])*
- **[Topic]**: [What happened/changed] *(Source: [meeting/email/slack], [date])*
- ...
```

### Page 2: Operational Imperatives (~600 words)

```markdown
---

## Critical Success Factors

[3-5 factors that must go right for the project to succeed. Update based on recent discussions - what are people worried about? What's getting attention?]

1. **[Factor 1]**: [Why it matters, current status]
2. **[Factor 2]**: [Why it matters, current status]
...

## Immediate Priorities (Next 2 Weeks)

| Priority | Owner | Status | Dependencies | Source |
|----------|-------|--------|--------------|--------|
| [Specific task/deliverable] | [Name] | [New/In Progress/Blocked/Complete] | [If any] | [Where identified] |
| ... | ... | ... | ... | ... |

## Medium-Term Milestones (Next 2-3 Months)

1. **[Milestone 1]** - Target: [Date]
   - Current progress: [Status description]
   - Key remaining work: [What's left]
   - Risks: [If any identified]

2. **[Milestone 2]** - Target: [Date]
   - Current progress: [Status]
   - Key remaining work: [What's left]
   - Risks: [If any]

...
```

### Page 3: Team Assignments & Open Items (~400 words + tables)

```markdown
---

## Weekly To-Do Lists by Team Member

### [Team Member 1 Name] - [Role]
- [ ] **[High priority]**: [Task description] *(Due: [date if known])*
- [ ] [Medium priority]: [Task description]
- [ ] [Lower priority]: [Task description]

### [Team Member 2 Name] - [Role]
- [ ] [Task 1]
- [ ] [Task 2]
...

### Unassigned Items
- [ ] [Task needing assignment] *(Suggested owner: [name or role])*

## Decisions Requiring Resolution

| Decision Needed | Context | Stakeholders | Target Date |
|-----------------|---------|--------------|-------------|
| [What needs to be decided] | [Brief background] | [Who should be involved] | [When needed] |
| ... | ... | ... | ... |

## Blockers & Risks

| Blocker/Risk | Impact | Owner | Mitigation |
|--------------|--------|-------|------------|
| [Issue description] | [High/Medium/Low] | [Who's responsible] | [What's being done] |
| ... | ... | ... | ... |

---

*Sources: [N] Slack messages, [N] emails, [N] meeting transcripts, [N] document updates*
*Data coverage: [START_DATE] to [END_DATE]*
```

## Hard Rules

1. **Source Attribution**: Every factual claim must have a source reference
2. **No Fabrication**: If data doesn't support a claim, write "[Insufficient data]"
3. **Team Member Matching**: Only list people from the project's team config
4. **Actionable To-Dos**: Each must have verb + object, be specific enough to act on
5. **Word Limits**: Respect the approximate limits for each page

## Output

Save to: `projects/$ARGUMENTS/overviews/[YYYY-WW]-overview.md`

Where YYYY-WW is the ISO week number (e.g., 2026-06 for week 6 of 2026).

## Quality Checklist

- [ ] All three pages complete
- [ ] Objectives pulled from objectives.md
- [ ] Key developments have source citations
- [ ] To-dos are specific and assigned
- [ ] Decisions and blockers tables populated
- [ ] Word limits approximately respected
