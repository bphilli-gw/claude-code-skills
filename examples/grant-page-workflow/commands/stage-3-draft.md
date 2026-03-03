# Stage 3: Edited Draft (Orchestrator)

This stage produces the full grant page draft by running six focused sub-stages in sequence, then assembling the final draft.

## Prerequisites

Before running Stage 3, ensure Stages 0-2 have been completed:
- `output/[grant-name]/0-readiness-assessment.md`
- `output/[grant-name]/1-extraction.md`
- `output/[grant-name]/2-section-plan.md`

---

## Sub-Stage Workflow

Stage 3 is broken into six focused sub-stages for consistency:

```
Stage 3a: Opening (Header + In a nutshell)
    ↓
Stage 3b: Background (Organization + Intervention)
    ↓
Stage 3c: Grant Details (The grant + Budget)
    ↓
Stage 3d: Case for the Grant (+ Cost-effectiveness)
    ↓
Stage 3e: Risks and Reservations
    ↓
Stage 3f: Closing Sections (Follow up, Forecasts, Process, Disclosures)
    ↓
Assembly: Combine into 3-draft.md
```

---

## Running the Sub-Stages

### Option A: Run All Sub-Stages Automatically

Run each sub-stage in sequence:

1. `/stage-3a-opening` → produces `3a-opening.md`
2. `/stage-3b-background` → produces `3b-background.md`
3. `/stage-3c-grant-details` → produces `3c-grant-details.md`
4. `/stage-3d-case` → produces `3d-case.md`
5. `/stage-3e-risks` → produces `3e-risks.md`
6. `/stage-3f-closing` → produces `3f-closing.md`

Then assemble the final draft.

### Option B: Run Sub-Stages with Review Points

If you want to review between sub-stages, run each command separately and review output before proceeding.

---

## Assembly Instructions

After all sub-stages are complete, assemble the final draft:

### 1. Create the Combined Draft

Read all sub-stage outputs and combine them in order:

```markdown
# [Header from 3a]

[Publication note from 3a]

**In a nutshell**
[Content from 3a]

## The organization
[Content from 3b]

## The intervention
[Content from 3b]

### Does [intervention] work?
[Content from 3b]

## The grant
[Content from 3c]

### Budget for grant activities
[Content from 3c]

## The case for the grant
[Content from 3d]

## Risks and reservations
[Content from 3e]

## Plans for follow up
[Content from 3f]

## Internal forecasts
[Content from 3f]

## Our process
[Content from 3f]

## Relationship disclosures
[Content from 3f]

## Sources
[Content from 3f]
```

### 2. Verify Consistency Across Sections

After assembly, check:
- [ ] Grant amount consistent across nutshell, grant section, budget
- [ ] Organization name spelled consistently throughout
- [ ] "(more)" links in nutshell point to actual sections
- [ ] Reasons in nutshell align with Case for Grant sections
- [ ] Reservations in nutshell align with Risks sections
- [ ] No duplicate content between sections
- [ ] Footnote numbers are sequential (renumber if needed)

### 3. Compile Footnotes

Gather all footnotes from sub-stages and renumber sequentially at the end of the document.

### 4. Add Draft Summary

At the top of `3-draft.md`, add:

```markdown
# Stage 3: Complete Draft

**Total word count:** [X]
**Total footnotes:** [N]
**Sub-stages completed:** 3a, 3b, 3c, 3d, 3e, 3f

**Flags requiring attention:**
- [List all FLAG items from sub-stages]

**Consistency checks:**
- [ ] Grant amount: $X (verified consistent)
- [ ] "(more)" links: [N] links, all resolved
- [ ] Footnotes: renumbered 1-[N]

---

[Full assembled grant page below]
```

---

## Output Location

Save assembled draft to: `output/[grant-name]/3-draft.md`

Sub-stage outputs remain in:
- `output/[grant-name]/3a-opening.md`
- `output/[grant-name]/3b-background.md`
- `output/[grant-name]/3c-grant-details.md`
- `output/[grant-name]/3d-case.md`
- `output/[grant-name]/3e-risks.md`
- `output/[grant-name]/3f-closing.md`

---

## Hard Rules Reference

These rules are embedded in each sub-stage, but for reference:

1. **Source discipline:** Facts from CA or its cited public sources only
2. **Numerics:** Exact match with CA
3. **Sensitivity:** No internal content
4. **Voice:** Clear GiveWell voice with "we"
5. **Vagueness ban:** No "transformative," "impactful," "significant" without comparator
6. **Anti-redundancy:** No preamble lists, one home per fact
7. **Links:** All "(more)" links must resolve to real sections

---

## Troubleshooting

**If sub-stages are inconsistent:**
- Re-run the inconsistent sub-stage
- Check that it read the previous outputs

**If "(more)" links don't resolve:**
- Check anchor format: lowercase, hyphens, no special characters
- Verify section exists in assembled draft

**If word count is too long/short:**
- Compare to similar grants in Stage 4 comparison audit
- Adjust detail level in relevant sub-stage
