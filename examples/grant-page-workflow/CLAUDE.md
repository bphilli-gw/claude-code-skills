# GiveWell Grant Page Writer

This project contains an AI workflow for drafting publishable grant pages from GiveWell's internal Conditional Approval (CA) documents.

## Project Structure

```
grant-page-writer/
├── CLAUDE.md                 # This file - project instructions
├── context/                  # Reference documents
│   ├── GiveWell Style Guide (Claude).md
│   ├── Legibility guidance_ grants pages, IRs, and simple CEAs.md
│   ├── [TEMPLATE] Grant Page for [grant].md
│   ├── Template for AI to draft a grant page from a CA.md
│   └── example-grant-pages/  # Example published grant pages (for comparison audit)
├── feedback/                 # Grantmaker feedback on drafts (for process improvement)
├── input/                    # Place CA documents here
│   └── processed/            # Move completed CAs here
├── output/                   # Stage outputs organized by grant
│   └── [grant-name]/
│       ├── 0-readiness-assessment.md
│       ├── 1-extraction.md
│       ├── 2-section-plan.md
│       ├── 3-draft.md
│       ├── 4-qc-audit.md
│       ├── 5-final-grant-page.md
│       └── 5-publication-checklist.md
└── .claude/
    └── commands/             # Slash commands for each stage
```

## Quick Start

1. **Prepare the CA:** Copy the Conditional Approval document as markdown into `input/`
2. **Run the workflow:** Use `/full-workflow input/[ca-filename].md`
3. **Review each stage:** The workflow pauses after each stage for your approval
4. **Get the final page:** Find publication-ready output in `output/[grant-name]/`

## Available Commands

| Command | Description |
|---------|-------------|
| `/full-workflow [ca-path]` | Run complete 6-stage workflow with checkpoints |
| `/stage-0-assess [ca-path]` | Stage 0: Publication Readiness Assessment |
| `/stage-1-extract` | Stage 1: Content Extraction & Gap Analysis |
| `/stage-2-plan` | Stage 2: Section Plan & Information Design |
| `/stage-3-draft` | Stage 3: Edited Draft (orchestrates sub-stages) |
| `/stage-4-qc` | Stage 4: Quality Control (10 audits) |
| `/download-doc [url-or-id]` | Download Google Doc as markdown with comments |
| `/stage-5-finalize` | Stage 5: Finalization & Packaging |

### Stage 3 Sub-Commands (for finer control)

| Command | Description |
|---------|-------------|
| `/stage-3a-opening` | Header + In a nutshell |
| `/stage-3b-background` | The organization + The intervention |
| `/stage-3c-grant-details` | The grant + Budget breakdown |
| `/stage-3d-case` | Case for the grant + Cost-effectiveness |
| `/stage-3e-risks` | Risks and reservations |
| `/stage-3f-closing` | Follow up, Forecasts, Process, Disclosures, Sources |

## Workflow Stages

### Stage 0: Publication Readiness Assessment
Analyzes the CA to determine work required:
- Section-by-section quality assessment
- Disposition codes (USE/EDIT/SUPPLEMENT/DRAFT/OMIT)
- Footnote conversion plan
- Sensitivity scan
- Overall readiness verdict

### Stage 1: Content Extraction & Gap Analysis
Systematically extracts usable content:
- Quote passages with edit levels
- Identify gaps per template section
- Build Claim-Evidence Map for auditing

### Stage 2: Section Plan & Information Design
Plans the grant page structure:
- Purpose and key points per section
- Evidence mapping
- Presentation format (prose vs. bullets vs. tables)
- Cost-effectiveness table design

### Stage 3: Edited Draft
Produces the full draft through six focused sub-stages:
- **3a: Opening** - Header + In a nutshell (accessible summary)
- **3b: Background** - Organization + Intervention context
- **3c: Grant Details** - The grant + Budget breakdown
- **3d: Case** - Case for the grant + Cost-effectiveness analysis
- **3e: Risks** - Risks and reservations
- **3f: Closing** - Follow up, Forecasts, Process, Disclosures

Each sub-stage has hard rules embedded for consistency. Sub-stages are assembled into the final `3-draft.md`.

### Stage 4: Quality Control
Ten explicit pass/fail audits:
1. Numerics audit (numbers match CA)
2. Vagueness lint (no banned phrases)
3. Footnote audit (all public sources, no "(unpublished)" tags)
4. Sensitivity audit (no internal content)
5. Preservation audit (minimal rewriting)
6. Template compliance (no Summary section, anti-redundancy checks)
7. Style guide compliance
8. Legibility check
9. Comparison audit - compare against similar published grant pages
10. Link validation - verify all (more) links resolve to real sections

### Stage 5: Finalization & Packaging
Produces publication-ready outputs:
- Applies all QC fixes
- Final polish and verification
- Publication-ready markdown
- Publication checklist for handoff

## Hard Rules

These rules are enforced throughout the workflow:

1. **Source discipline:** Facts from CA or public sources cited in CA only. Never cite the CA itself. Never fabricate or extrapolate.
2. **Numerics:** Exact match with CA (units, precision preserved).
3. **Sensitivity:** No internal emails, individual evaluations, negotiation details, unpublished parameters.
4. **Voice:** Clear, direct GiveWell voice with "we." Short paragraphs. Define terms.
5. **Vagueness ban:** No "transformative," "impactful," "significant" without comparator, etc.
6. **Preserve quality:** Adapt good CA prose; don't replace with generic summaries.
7. **No Summary section:** Grant pages go directly from "In a nutshell" to main sections (The organization, The intervention, etc.). No separate Summary with subsections.
8. **Anti-redundancy:** No preamble lists before subsections. Each fact has one home. Reasons must be reasons, not descriptions.
9. **Working links:** All "(more)" links must resolve to real section anchors. Never output `([more](undefined))`.

## Reference Documents

Located in `context/`:

- **Grant page template:** Standard structure for all grant pages
- **Legibility guidance:** What makes grant pages clear and useful
- **Style guide:** GiveWell writing conventions (American English, Oxford commas, etc.)
- **Example pages:** Published grant pages for comparison audits

### How Guidelines Are Used

**Key rules are distilled directly into slash commands** rather than asking Claude to "consult" reference documents. This ensures:
- Rules are applied consistently every time
- No risk of missing important guidance buried in long documents
- Stage-appropriate rules (drafting rules in Stage 3, QC rules in Stage 4)

**Example pages are used for comparison audits** in Stage 4:
- Select 1-2 similar published pages (by grant size, type, intervention)
- Compare length, structure, depth, and tone
- Calibrate the draft to match published quality standards

## Tips for Best Results

1. **Read the CA first** - Understand the grant before running the workflow
2. **Review each stage** - Catch issues early rather than at QC
3. **Provide feedback** - If a stage's output needs adjustment, explain what to change
4. **Use stage commands** - Re-run individual stages if needed
5. **Check blockers** - Resolve any BLOCKER flags before finalizing

## Feedback & Iteration

The `feedback/` folder contains grantmaker feedback on draft outputs. This feedback was used to refine the workflow rules. Key learnings incorporated:

- Eliminated Summary section (redundant with nutshell)
- Added anti-redundancy rules (no preamble lists, one home per fact)
- Added link validation audit
- Updated footnote rules (link to docs, don't tag as "unpublished")
- Added public framing rules (simplify internal jargon)
