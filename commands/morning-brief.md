---
description: Daily check-in — calendar, priorities, Asana triage, and goal alignment in a 2-minute read
---

You are running a daily morning brief. This is a lightweight check-in — no messages sent, no scheduling. Just: "here's what matters today."

## Step 1: Gather context (in parallel)

### Calendar
Pull today's events and tomorrow's events. Flag:
- Meetings that need prep (external calls, 1:1s with manager, presentations)
- Back-to-back blocks with no break
- Anything outside preferred meeting windows

### Asana tasks
Pull all incomplete Asana tasks assigned to the user. Use these for both the priority list and the board triage.

### Goals check
- Review current goals and flag any that are:
  - Due soon and not started
  - Blocked or at risk based on what you see in projects

### Email & Slack (only if actionable)
Scan email and Slack (relevant DMs, team channels) in parallel with the above. **Only include in the brief if there's something that actually needs attention or a response.** Skip these sections entirely if nothing is urgent — don't pad the brief with FYI items.

## Step 2: Present the brief

Format as a clean, scannable summary. **Only include sections that have content worth surfacing.** Skip empty or low-value sections.

```
Good morning — here's your brief for [Day, Month Date].

CALENDAR
- [Time] [Meeting] — [prep note if needed]
- [Time] [Meeting]
- Focus blocks: [available time for deep work]
- Tomorrow: [preview if notable]

PRIORITIES
Based on Asana tasks due today/overdue, meetings, and active projects, here's what matters most:
1. [Priority item — with context on why it's top]
2. [Priority item]
3. [Priority item]

ASANA TRIAGE
[Overdue tasks that need re-dating or closing]
[Tasks in the wrong section — recommend moves]

GOALS
- [Any goals that need attention — only flag what's at risk or blocked]

OTHER
- [Actionable email, Slack messages, project status changes — only if they exist]
```

If any source (Calendar, Gmail, Slack, Drive, Asana) failed or returned an auth error, add a section at the end:

```
SOURCES UNAVAILABLE
- [Source]: [error summary]
```

Keep it to a 2-minute read. Don't editorialize — just surface what matters and let the user decide what to act on.

## Step 3: Offer next steps

End with:
> Anything you want to dig into?
