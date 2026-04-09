# Set Up Your Second Brain

Bootstrap a Claude Code "second brain" — a project folder that gives Claude persistent context about your work, so it can act as a strategic partner across conversations.

## What This Creates

By the end of this skill, you'll have a project folder with:
- `CLAUDE.md` — personalized instructions telling Claude who you are, what you're working on, and how to help
- `preferences.md` — your app-specific rules (calendar, Slack, Asana, email)
- `people.md` — key contacts and working relationships
- `goals.md` — current priorities and success criteria
- `active-projects.md` — what you're actively working on, with status and context
- `meetings/` — folder for meeting notes (check-ins, external calls, etc.)
- `weekly-plans/` — folder for weekly priority logs

## How It Works

This is a two-phase process:
1. **Discovery** — Claude reads your Drive, Slack, Asana, and Calendar to learn about your work (read-only, nothing is modified)
2. **Interview** — Claude asks you questions about things it couldn't find automatically, then generates all the files

---

## Phase 1: Automated Discovery

Go through each source below. Summarize what you find — don't dump raw data into files yet. You're building a picture of this person's work life.

**Important**: All discovery is read-only. Do not create, modify, or send anything in any external tool during this phase. If a tool isn't connected, skip that source and note what you missed — you'll cover it in the interview.

### 1a. Calendar

Using Google Calendar MCP tools:
- List all calendars the user has access to
- Pull events from the past 2 weeks and next 2 weeks
- Identify:
  - **Recurring 1:1s** — who are they with? (likely manager, direct reports, key collaborators)
  - **Recurring team meetings** — what teams is this person on?
  - **External calls** — any pattern of external meetings?
  - **Focus/deep work blocks** — do they block time?
  - **Meeting density** — roughly how many meetings per day?

### 1b. Asana

Using Asana MCP tools:
- List workspaces, then get the user's tasks (focus on incomplete tasks)
- Look at My Tasks sections to understand their time-horizon organization
- Identify:
  - **Active projects** — what are they assigned to? What sections/boards?
  - **Recent completions** — what did they finish in the last 2-4 weeks?
  - **Task patterns** — do they use subtasks? Due dates? Custom fields?
  - **Collaborators** — who appears most often on shared tasks?
  - **Projects they're a member of** — what teams/workstreams do these map to?

### 1c. Slack

Using Slack MCP tools:
- Search for recent messages from the user (last 2 weeks)
- Identify:
  - **Most active channels** — where do they post most?
  - **DM patterns** — who do they message most? (don't read content, just note frequency/contacts)
  - **Key threads** — any long threads suggesting active projects or decisions?
  - **Tone** — casual? formal? emoji-heavy? (this informs Slack preferences later)

### 1d. Drive

Using Google Drive MCP tools:
- List recently modified files (last 30 days)
- Identify:
  - **Documents they're actively editing** — what topics/projects do these cover?
  - **Shared folders** — what team spaces do they have access to?
  - **Document types** — mostly Docs? Sheets? Slides? (suggests work style)
  - **Key documents** — anything that looks like a goals doc, project tracker, or team plan?

### 1e. Gmail

Using Gmail MCP tools:
- Search recent sent mail (last 2 weeks, just subjects and recipients — do not read email bodies unless the user explicitly approves)
- Identify:
  - **Key correspondents** — who do they email most?
  - **External contacts** — anyone outside the org?
  - **Email volume** — roughly how many sent per day?

---

## Phase 1 Summary

Before moving to the interview, present a summary to the user:

> **Here's what I've learned about your work so far:**
>
> - **Role**: [what you've inferred]
> - **Manager**: [from recurring 1:1]
> - **Teams**: [from meetings and Slack channels]
> - **Active projects**: [from Asana + Drive + Calendar]
> - **Key contacts**: [top 8-10 people you see everywhere]
> - **Tools & habits**: [what you noticed about how they work]
>
> **I wasn't able to find**: [list gaps — e.g., "your goals for this quarter," "what you'd want AI help with"]
>
> Does this look right? Anything I got wrong or missed?

Let them correct anything before proceeding.

---

## Phase 2: Interview

Ask the following questions **one group at a time** (don't dump all questions at once). Skip any that were already answered by discovery.

### Group 1: Role & Context
- What's your actual title and role? What do you spend most of your time on?
- Who's your manager? How often do you meet?
- Are you on any specific teams, pods, or working groups?
- What are your main goals or priorities this quarter?

### Group 2: Projects
- [Reference the project list from discovery] Is this accurate? Anything missing or wrong?
- For each active project: what's the current status and what's your role in it?
- Any projects you're about to start or that are winding down?

### Group 3: Working Style & Preferences
- When do you prefer to do focused work vs. meetings?
- Any calendar rules? (e.g., no meetings before 10am, no weekends)
- How do you prefer to communicate on Slack? (casual, professional, channel vs. DM preferences)
- Any email rules? (e.g., read-only for AI, specific people to always reply to quickly)
- How do you use Asana? (e.g., religiously, reluctantly, specific workflow)

### Group 4: What You Want Help With
- What would be most valuable for Claude to help you with day-to-day?
- Any recurring tasks that feel like a grind? (e.g., meeting prep, weekly updates, status reports)
- What information do you find yourself repeatedly looking up?
- Is there anything you explicitly do NOT want Claude doing? (e.g., sending messages, modifying documents)

---

## Phase 3: Generate Files

Based on everything gathered, create the project structure. Use the templates below as starting points — adapt them to match what you actually learned.

### Create the project folder

Ask the user where they want the project. Suggest: `~/Documents/[name]-second-brain/` or similar.

Create the folder structure:
```
[project-name]/
├── CLAUDE.md
├── preferences.md
├── people.md
├── goals.md
├── active-projects.md
├── meetings/
│   ├── check-ins/
│   └── external-calls/
└── weekly-plans/
```

### CLAUDE.md Template

```markdown
# Claude's Role: [Role Title]'s Strategic Partner

## Purpose

You are a strategic partner for [Name], helping with [primary use cases from interview]. This project serves as a "second brain" — it stores context about [Name]'s work so that Claude can provide informed help across conversations.

## About the User ([Name])

**Role & Responsibilities**:
- [Title] at [Org]
- [Key responsibilities — 3-5 bullets]

**Reporting Structure**:
- Reports to: [Manager]
- Coordinates with: [Key collaborators]

**Working Style**:
- [Key observations from discovery + interview]

**Current Projects** (as of [date]):
- [Project list with brief status]

## File Structure

[Document the actual structure created]

## Skills (Slash Commands)

[Leave blank or add /morning-brief if they install it]

## Working Principles

1. **Context-aware**: Reference [org name]'s mission and constraints
2. **Practical**: Focus on implementable suggestions
3. **Iterative**: Embrace learning and adaptation
4. **Respect boundaries**: [Any explicit "don't do this" rules from interview]
```

### preferences.md Template

```markdown
# Preferences & Policies

Rules for how Claude should handle app-specific actions on [Name]'s behalf.

## Calendar
- **Preferred meeting times**: [from interview]
- **Avoid**: [from interview]
- **Timezone**: [timezone]

## Asana
- [Task assignment rules]
- [Section/project conventions]

## Slack
- **Tone**: [from discovery]
- **Don't**: [any restrictions]

## Gmail
- **Read-only by default**: Don't draft or send emails without explicit approval
- [Any additional rules]

## General
- **Ask before sending**: Always show draft messages before sending
- **Decisions need approval**: Never make strategic decisions without confirming
```

### people.md Template

```markdown
# People Directory

Quick reference for key contacts.

## Core Working Group

| Name | Role | Relationship | Notes |
|------|------|-------------|-------|
| [Manager] | [Title] | Manager | [Meeting cadence] |
| [Collaborators from discovery] | ... | ... | ... |

## Other Frequent Contacts

| Name | Role | Context |
|------|------|---------|
| [From Slack/email/calendar patterns] | ... | ... |
```

### goals.md Template

```markdown
# Goals & Priorities

*Last updated: [date]*

## This Quarter ([Q_ 20__])

1. [Goal from interview]
   - Success looks like: [criteria]
   - Key milestones: [if mentioned]

2. [Goal]
   - ...
```

### active-projects.md Template

```markdown
# Active Projects

*Last updated: [date]*

| Project | Status | My Role | Key Contacts | Notes |
|---------|--------|---------|-------------|-------|
| [From discovery + interview] | ... | ... | ... | ... |
```

---

## Phase 4: Wrap Up

1. **Show the user what you created** — list every file with a one-line summary
2. **Suggest next steps**:
   - "Try asking Claude a question about your work to see if the context helps"
   - "Consider installing the `/morning-brief` skill for a daily check-in"
   - "Update `active-projects.md` whenever something changes — Claude will pick it up automatically"
   - "After meetings, drop a transcript in the project folder and ask Claude to process it"
3. **Remind them**: "This works because Claude reads `CLAUDE.md` at the start of every conversation in this folder. The more you keep these files current, the more useful it gets."
