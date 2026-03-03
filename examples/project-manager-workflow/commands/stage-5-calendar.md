---
description: Stage 5 - Push to-dos to calendars and send notifications
argument-hint: <project-slug>
---

# Stage 5: Calendar Integration & Notifications

Create calendar reminders for to-dos and notify the team via Slack.

## Arguments

- **$ARGUMENTS**: Required project slug

## Prerequisites

- Stage 3 to-dos extracted: `projects/$ARGUMENTS/summaries/[DATE]-todos.md`
- Team member calendar configs in `config/team-members.yaml`
- Project notification channel in `projects/$ARGUMENTS/config.yaml`

## Your Task

### 1. Load To-Dos and Team Config

Read:
- `projects/$ARGUMENTS/summaries/[DATE]-todos.md` for assigned to-dos
- `config/team-members.yaml` for calendar integration details
- `projects/$ARGUMENTS/config.yaml` for notification channel

### 2. Create Calendar Events

For each assigned to-do with urgency "This Week" or "Next 2 Weeks":

**Google Calendar (via hardened-workspace MCP):**
```
Title: [Project] [Task summary - first 50 chars]
Description:
  Task: [Full task description]
  Source: [Where identified]
  Project: [Project name]
  Priority: [Urgency + Importance]

Start: [Due date, or end of urgency window]
Duration: 30 minutes (as reminder block)
Reminders:
  - 1 day before (popup)
  - Morning of (email)
Color: Red for Critical/High, Yellow for Medium, Green for Low
```

**Event Creation Logic:**
- If task has explicit deadline → use that date
- If urgency is "This Week" → set for Friday of current week
- If urgency is "Next 2 Weeks" → set for Friday of next week
- Skip creating events for "This Month" items (too far out)

### 3. Post to Slack Notification Channel

Use Slack MCP to post to the project's notification channel:

```
:clipboard: *[Project Name] Weekly Intelligence Brief*
:calendar: Week of [DATE]

*Top Developments:*
:star: [Development 1]
:star: [Development 2]
:star: [Development 3]

*This Week's Priorities:*
:one: [Priority 1] - Owner: @[person]
:two: [Priority 2] - Owner: @[person]
:three: [Priority 3] - Owner: @[person]

*Team To-Do Summary:*
• <@[slack_user_id]>: [N] items ([M] high priority)
• <@[slack_user_id]>: [N] items ([M] high priority)

:link: Full overview: [Link to overview file or Google Doc]
:brain: Project memory: [Link to decisions log]
```

### 4. Individual DMs (Optional)

If team members have `notification_preferences.weekly_summary: true`:

```
:wave: Hi [Name]!

Here are your to-dos for *[Project Name]* this week:

*High Priority:*
:red_circle: [Task 1]
:red_circle: [Task 2]

*Other Items:*
:yellow_circle: [Task 3]
:white_circle: [Task 4]

Full overview: [Link]
```

### 5. Log Notifications

Save a record of what was sent to `projects/$ARGUMENTS/summaries/[DATE]-notifications.log`:

```
Notifications Log - [DATE] [TIME]
Project: [Project Name]

Calendar Events Created:
- [Person]: [Task] → Event ID: [id], Due: [date]
- [Person]: [Task] → Event ID: [id], Due: [date]

Slack Notifications:
- Channel #[name]: Posted summary at [timestamp]
- DM to [Person]: Sent at [timestamp]
- DM to [Person]: Sent at [timestamp]

Errors:
- [Any errors encountered]
```

## Calendar Event Deduplication

Before creating a calendar event:
1. Check if an event with similar title already exists in that time window
2. If yes, update the existing event rather than creating duplicate
3. Note updated vs. created in the log

## Error Handling

- If calendar MCP unavailable: Log error, continue with Slack notifications
- If Slack MCP unavailable: Log error, note that manual notification needed
- If a specific user's calendar fails: Log and continue with others
- Always produce notification log even if partial success

## Output

- Calendar events created for team members
- Slack message posted to notification channel
- Individual DMs sent (if configured)
- Log file: `projects/$ARGUMENTS/summaries/[DATE]-notifications.log`

## Quality Checklist

- [ ] To-dos with deadlines have calendar events
- [ ] Slack summary posted to correct channel
- [ ] Team members @mentioned correctly
- [ ] DMs sent to those who opted in
- [ ] Notification log created
- [ ] No duplicate calendar events created
