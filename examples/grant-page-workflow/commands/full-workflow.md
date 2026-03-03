# Full Grant Page Workflow

This command guides you through the complete workflow for drafting a grant page from a Conditional Approval document.

## Setup

**Argument:** Path to the CA document (e.g., `input/malaria-consortium-chad-ca.md`)

If no argument provided: $ARGUMENTS

---

## Before Starting

1. **Verify the CA is in the input/ folder** as a markdown file
2. **Read the CA yourself first** to understand the grant
3. **Create the output folder** for this grant: `output/[grant-name]/`

---

## Workflow Overview

```
Stage 0: Publication Readiness Assessment
    ↓
Stage 1: Content Extraction & Gap Analysis
    ↓
Stage 2: Section Plan & Information Design
    ↓
Stage 3: Edited Draft
    ↓
Stage 4: Quality Control (9 audits)
    ↓
Stage 5: Finalization & Packaging
```

---

## Stage 0: Publication Readiness Assessment

- Analyze CA quality section-by-section
- Identify content dispositions (USE/EDIT/SUPPLEMENT/DRAFT/OMIT)
- Create footnote conversion plan
- Scan for sensitivity issues
- Provide overall verdict

**Output:** `output/[grant-name]/0-readiness-assessment.md`

**Checkpoint:** Review assessment. Proceed? [yes/no]

---

## Stage 1: Content Extraction & Gap Analysis

- Extract usable passages from CA
- Mark edit levels needed
- Identify gaps for each template section
- Build Claim-Evidence Map

**Output:** `output/[grant-name]/1-extraction.md`

**Checkpoint:** Review extraction. Any clarifications needed? [yes/no]

---

## Stage 2: Section Plan & Information Design

- Plan each section's purpose and key points
- Map evidence to claims
- Design presentation format
- Plan cost-effectiveness table (if applicable)
- Design information flow

**Output:** `output/[grant-name]/2-section-plan.md`

**Checkpoint:** Review plan. Approve approach? [yes/no]

---

## Stage 3: Edited Draft

Stage 3 is broken into six focused sub-stages for consistency:

```
3a: Opening (Header + In a nutshell)
3b: Background (Organization + Intervention)
3c: Grant Details (The grant + Budget)
3d: Case for the Grant (+ Cost-effectiveness)
3e: Risks and Reservations
3f: Closing Sections (Follow up, Forecasts, Process, Disclosures)
→ Assembly into final draft
```

Each sub-stage:
- Focuses on specific sections only
- Has hard rules embedded (no cross-referencing needed)
- Produces a separate output file

**Sub-stage outputs:**
- `output/[grant-name]/3a-opening.md`
- `output/[grant-name]/3b-background.md`
- `output/[grant-name]/3c-grant-details.md`
- `output/[grant-name]/3d-case.md`
- `output/[grant-name]/3e-risks.md`
- `output/[grant-name]/3f-closing.md`

**Final output:** `output/[grant-name]/3-draft.md` (assembled from sub-stages)

**Checkpoint:** Review draft. Any revisions needed? [yes/no]

---

## Stage 4: Quality Control

Ten explicit pass/fail audits:
1. Numerics audit (numbers match CA)
2. Vagueness lint (no banned phrases)
3. Footnote audit (all public sources)
4. Sensitivity audit (no internal content)
5. Preservation audit (minimal rewriting)
6. Template compliance (no Summary section - nutshell → main sections)
7. Style guide compliance
8. Legibility check
9. Comparison audit - compare against similar published grant pages
10. Link validation - all (more) links resolve to real sections

**Output:** `output/[grant-name]/4-qc-audit.md`

**Checkpoint:** Review QC results. Address any failures before proceeding.

---

## Stage 5: Finalization & Packaging

- Apply all QC fixes
- Final polish (flow, balance, reader experience)
- Finalize footnotes
- Verify acceptance criteria
- Generate publication-ready markdown
- Create publication checklist

**Output:**
- `output/[grant-name]/5-final-grant-page.md`
- `output/[grant-name]/5-publication-checklist.md`

**Complete!**

---

## How to Use

### Option A: Run Full Workflow (Recommended)
Use this command and work through all stages sequentially with review checkpoints.

### Option B: Run Individual Stages
If you need to re-run or skip stages:
- `/stage-0-assess [ca-path]` - Run Stage 0 only
- `/stage-1-extract` - Run Stage 1 only
- `/stage-2-plan` - Run Stage 2 only
- `/stage-3-draft` - Run Stage 3 (all sub-stages + assembly)
- `/stage-4-qc` - Run Stage 4 only
- `/stage-5-finalize` - Run Stage 5 only

### Option C: Run Stage 3 Sub-Stages Individually
For finer control over drafting:
- `/stage-3a-opening` - Header + In a nutshell
- `/stage-3b-background` - Organization + Intervention
- `/stage-3c-grant-details` - The grant + Budget
- `/stage-3d-case` - Case for the grant + Cost-effectiveness
- `/stage-3e-risks` - Risks and reservations
- `/stage-3f-closing` - Follow up, Forecasts, Process, Disclosures

### Option D: Resume Workflow
If you stopped mid-workflow, tell me which stage to resume from.

---

## Reference Documents

These are available in `context/`:
- **Template:** `[TEMPLATE] Grant Page for [grant].md`
- **Legibility guidance:** `Legibility guidance_ grants pages, IRs, and simple CEAs.md`
- **Style guide:** `GiveWell Style Guide (Claude).md`
- **Prompting guidance:** `Template for AI to draft a grant page from a CA.md`
- **Example grant pages:** `context/example-grant-pages/`

---

## Ready to Begin?

Please confirm:
1. CA document location: [path]
2. Grant name for output folder: [name]

Then I'll begin with Stage 0: Publication Readiness Assessment.
