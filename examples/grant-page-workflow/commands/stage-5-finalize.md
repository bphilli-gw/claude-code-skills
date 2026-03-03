# Stage 5: Finalization & Packaging

You are a GiveWell editor finalizing the grant page for publication. Apply all QC fixes, perform final polish, and produce the publication-ready document.

## Prerequisites

Before running this stage, ensure Stages 0-4 have been completed and all blockers resolved. Read:
- `output/[grant-name]/3-draft.md`
- `output/[grant-name]/4-qc-audit.md`

**STOP** if the QC audit shows unresolved blockers. Those must be addressed first.

---

## Step 1: Apply QC Fixes

Work through each issue identified in Stage 4:

### Numerics Fixes
[ ] Fix 1: [Description]
[ ] Fix 2: [Description]

### Vagueness Rewrites
[ ] Rewrite 1: [Original → Fixed]
[ ] Rewrite 2: [Original → Fixed]

### Footnote Corrections
[ ] Correction 1: [Description]
[ ] Correction 2: [Description]

### Sensitivity Removals
[ ] Removal 1: [Description]
[ ] Removal 2: [Description]

### Style Guide Fixes
[ ] Fix 1: [Description]
[ ] Fix 2: [Description]

---

## Step 2: Final Polish

### Logical Flow Check
Read the document start-to-finish and verify:
- [ ] "In a nutshell" accurately summarizes the full page
- [ ] Summary sections flow logically
- [ ] "More" links point to correct sections
- [ ] No redundant information between sections
- [ ] Transitions between sections are smooth

### Balance Check
- [ ] Benefits and risks are presented in balanced proportion
- [ ] Uncertainty is communicated appropriately (not over- or understated)
- [ ] The tone is objective and evidence-based

### Reader Experience
- [ ] A reader landing on this page can quickly understand the grant
- [ ] Key information is findable without extensive scrolling
- [ ] Technical terms are defined on first use

---

## Step 3: Footnote Finalization

### Renumber Footnotes
Ensure footnotes are numbered sequentially from 1, in order of first appearance.

### Verify All Links
For each linked source, confirm:
- [ ] Link resolves to the correct page
- [ ] CEA links point to current version
- [ ] Conversation notes are publicly accessible
- [ ] "More" links point to correct anchors

### Footnote Format Check
Each footnote should follow this format:
```
[^N]: "Direct quote from source." Source Name, p. X.
```
or
```
[^N]: Source Name, description of where to find information.
```

---

## Step 4: Final Acceptance Criteria

Explicitly verify each criterion is met:

| Criterion | Met? | Evidence |
|-----------|------|----------|
| No unsupported claims | | |
| No citations to the CA | | |
| All footnotes cite public sources from CA | | |
| All numbers match CA (units/precision preserved) | | |
| No vague/headline language | | |
| No sensitive/internal information | | |
| Conforms to GiveWell style guide | | |
| Conforms to legibility guidance | | |
| All template sections present or justified omission | | |
| Required disclaimers included | | |

**ALL CRITERIA MUST BE MET BEFORE FINALIZING**

---

## Step 5: Generate Final Outputs

### Output 1: Publication-Ready Markdown

Create the final grant page as clean markdown:

```markdown
# [Organization] — [Purpose of Grant] ([Month Year])

*Note: This page summarizes the rationale behind a GiveWell grant to [organization]. [Organization] staff reviewed this page prior to publication.*

| In a nutshell |
| :---- |
| [Content] |

*Published: [Date]*

[Table of Contents]

[Full page content with proper headers, formatting, and footnotes]
```

Save to: `output/[grant-name]/5-final-grant-page.md`

### Output 2: Publication Checklist

Create a checklist for the publication team:

```markdown
# Publication Checklist for [Grant Name]

## Document Info
- Grant: [Organization] - [Purpose]
- Amount: $[X]
- Drafted: [Date]
- Word count: [X]
- Footnotes: [X]

## Pre-Publication Checks
- [ ] Grantee review completed
- [ ] Pod lead review completed
- [ ] All links verified working
- [ ] Sources spreadsheet completed
- [ ] Images/tables render correctly

## Known Issues / Notes for Reviewer
- [Any issues the publication team should know about]

## Contacts
- Grant investigator: [Name]
- Drafter: [AI-assisted]
```

Save to: `output/[grant-name]/5-publication-checklist.md`

---

## Summary Statistics

At the top of the final output, include:

```markdown
---
Grant: [Organization] — [Purpose]
Amount: $[X]
Funder: [Funder name]
Date: [Month Year]
Word count: [X]
Footnotes: [X]
Stages completed: 0-5
QC audits passed: 8/8
Blockers resolved: [X]
---
```

---

## Output Location

Save final outputs to:
- `output/[grant-name]/5-final-grant-page.md` (publication-ready page)
- `output/[grant-name]/5-publication-checklist.md` (handoff checklist)
