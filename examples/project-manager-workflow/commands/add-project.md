---
description: Initialize a new project for tracking
argument-hint: (interactive - will prompt for details)
---

# Add New Project

Create the directory structure and configuration for a new project.

## Process

This command will guide you through setting up a new project:

### 1. Gather Project Information

Ask the user for:
- **Project name**: Full name (e.g., "Malaria Vaccine Randomized Trial")
- **Project slug**: Short identifier, lowercase, hyphens (e.g., "malaria-vaccine-trial")
- **Team lead email**: Primary contact
- **Team members**: List of email addresses

### 2. Create Directory Structure

Create the following under `projects/[slug]/`:

```
projects/[slug]/
├── config.yaml          # Project configuration
├── objectives.md        # Long-run objectives (template)
├── raw/                 # Will hold raw data pulls
├── summaries/           # Will hold weekly summaries
├── overviews/           # Will hold 3-page overviews
└── memory/
    └── decisions-log.md # Initialize empty log
```

### 3. Create Configuration Template

Generate `projects/[slug]/config.yaml`:

```yaml
# [Project Name] Configuration
# Created: [DATE]

project:
  slug: "[slug]"
  name: "[Project Name]"
  created: "[DATE]"

# Configure your data sources below
sources:
  slack:
    channels: []          # Add Slack channel names, e.g., ["#project-channel"]
    keywords: []          # Optional: filter by keywords

  email:
    gmail:
      labels: []          # Add Gmail labels, e.g., ["Projects/Example"]
      from_domains: []    # Optional: filter by sender domain

  meetings:
    # Option 1: Local folder with transcript files
    local_folder: ""      # e.g., "C:/Users/.../Transcripts/"
    # Option 2: Google Drive folder
    drive_folder_id: ""   # e.g., "1ABC123xyz"
    file_patterns: ["*.txt", "*.md", "*.docx"]

  documents:
    google_docs:
      folder_ids: []      # Google Drive folder IDs
      document_ids: []    # Specific document IDs
    local_files:
      paths: []           # Local folder paths
      patterns: ["*.md", "*.tex"]

# Team members (must also be in config/team-members.yaml)
team:
  - email: "[team_lead_email]"
    name: "[Name]"
    role: "Team Lead"
    calendar_integration: "google"  # or "outlook"

# Add more team members:
#  - email: "other@example.org"
#    name: "Other Person"
#    role: "Role"
#    calendar_integration: "google"

# Output configuration
output:
  overview_doc_id: ""           # Optional: Google Doc ID for overview
  memory_doc_id: ""             # Optional: Google Doc ID for memory
  notification_channel: ""       # Slack channel for notifications
```

### 4. Create Objectives Template

Generate `projects/[slug]/objectives.md`:

```markdown
# [Project Name] - Long-Run Objectives

*Last updated: [DATE]*

## Mission

[Describe the overall mission/purpose of this project in 1-2 sentences]

## Strategic Objectives

### 1. [Objective 1]
[Description of this objective and why it matters]

### 2. [Objective 2]
[Description]

### 3. [Objective 3]
[Description]

## Key Milestones

| Milestone | Target Date | Status |
|-----------|-------------|--------|
| [Milestone 1] | [Date] | Not Started |
| [Milestone 2] | [Date] | Not Started |

## Success Criteria

- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

---

*This document should be updated manually as project objectives evolve.*
```

### 5. Initialize Decisions Log

Create `projects/[slug]/memory/decisions-log.md`:

```markdown
# [Project Name] - Decisions Log

This document contains weekly summaries of project activities, decisions, and discussions. Most recent entries appear first.

*Initialized: [DATE]*

---

[Weekly entries will be prepended here by Stage 4]
```

### 6. Add to Master Registry

Update `config/projects.yaml` to include the new project:

```yaml
projects:
  # ... existing projects ...

  - slug: "[slug]"
    name: "[Project Name]"
    active: true
    team_lead: "[team_lead_email]"
    team_members:
      - "[team_lead_email]"
      # Add other team member emails
```

### 7. Remind User of Next Steps

After creating the project structure, remind the user:

1. **Configure data sources**: Edit `projects/[slug]/config.yaml` to add:
   - Slack channels to monitor
   - Gmail labels to search
   - Document locations

2. **Write objectives**: Edit `projects/[slug]/objectives.md` with actual project goals

3. **Add team members**: Ensure all team members are in `config/team-members.yaml`

4. **Test the sync**: Run `/weekly-sync [slug]` to verify configuration

## Output

- New project directory created
- Configuration template generated
- Objectives template created
- Decisions log initialized
- Master registry updated
