# Stage 4: Quality Control

You are a GiveWell editor performing rigorous quality control on the draft grant page. This stage produces explicit pass/fail audits that must all pass before finalization.

## Prerequisites

Before running this stage, ensure Stages 0-3 have been completed. Read:
- The CA document in `input/`
- `output/[grant-name]/1-extraction.md` (for Claim-Evidence Map)
- `output/[grant-name]/3-draft.md`
- **1-2 comparable example grant pages** from `context/example-grant-pages/`

**Selecting comparison pages:** Choose examples that are similar to the current grant in:
- Grant size (small <$2M, medium $2-10M, large >$10M)
- Grant type (direct implementation, organizational development, technical assistance)
- Intervention area (if applicable)

---

## Audit 1: Numerics Audit

**Purpose:** Verify every number in the draft matches the CA exactly.

Create a Numbers Table:

| # | Number in Draft | Draft Location | Value in CA | CA Location | Pass/Fail |
|---|-----------------|----------------|-------------|-------------|-----------|
| 1 | | | | | |
| 2 | | | | | |

**Rules:**
- Every number must trace to the CA or a public source cited in the CA
- Units must match exactly
- Precision must be preserved (don't round $4.73 to $5)
- Percentages must match
- Date/year references must be accurate

**Result:** [ ] ALL PASS / [ ] FAILURES FOUND

If failures found, list corrections needed:
1. [Correction 1]
2. [Correction 2]

---

## Audit 2: Vagueness Lint

**Purpose:** Identify and rewrite any vague or banned language.

**Banned phrases to scan for:**
- "transformative"
- "impactful"
- "game-changing"
- "overall" (as filler)
- "it is important to note"
- "in summary"
- "significant" (without comparator)
- "substantial" (without comparator)
- Generic hedges without stated basis

**Scan results:**

| # | Flagged Phrase | Location | Original Sentence | Proposed Rewrite |
|---|---------------|----------|-------------------|------------------|
| 1 | | | | |
| 2 | | | | |

**Result:** [ ] ALL FIXED / [ ] FIXES NEEDED

---

## Audit 3: Footnote Audit

**Purpose:** Verify every footnote cites a public source, not the CA.

Create a Footnote Table:

| FN# | Claim Supported | Source Type | Source Name | Has Link? | Pass/Fail |
|-----|-----------------|-------------|-------------|-----------|-----------|
| 1 | | | | | |
| 2 | | | | | |

**Rules:**
- No citations to the CA itself
- All sources should have links (let reviewer decide what to redact)
- Do NOT use "(unpublished)" tags—link to the document and let reviewer handle
- Sources should match what the CA cited for the same claims
- Required disclaimers must be present (CEA disclaimer, cash benchmark)
- No footnotes in "In a nutshell" section

**Result:** [ ] ALL PASS / [ ] FAILURES FOUND

If failures found, list corrections needed:
1. [Correction 1]

---

## Audit 4: Sensitivity Audit

**Purpose:** Confirm all internal/sensitive content has been removed.

**Check for presence of:**
- [ ] Internal email references
- [ ] Names of individuals in evaluative context
- [ ] Negotiation details (amounts discussed, counteroffers)
- [ ] Unpublished model parameters
- [ ] Internal GiveWell process details not for publication
- [ ] Partner information marked confidential
- [ ] Draft document references

**Scan results:**

| # | Sensitive Content Found | Location | Resolution |
|---|------------------------|----------|------------|
| 1 | | | |

**Result:** [ ] ALL CLEAR / [ ] ISSUES FOUND

---

## Audit 5: Preservation Audit

**Purpose:** Verify that `USE` and `EDIT` sections weren't unnecessarily rewritten.

For each section marked `USE` or `EDIT` in Stage 3:

| Section | Disposition | CA Word Count | Draft Word Count | Change % | Justified? |
|---------|-------------|---------------|------------------|----------|------------|
| | | | | | |

**Rules:**
- Word count increases >50% signal potential unnecessary rewriting
- Changes should be surgical (footnote conversion, sensitivity removal, clarity)
- Good CA prose should be preserved, not replaced with generic summaries

**Result:** [ ] CHANGES JUSTIFIED / [ ] REVIEW NEEDED

If review needed, list concerns:
1. [Section]: [Concern]

---

## Audit 6: Template Compliance

**Purpose:** Verify all required sections are present and properly formatted.

**IMPORTANT:** There is NO separate "Summary" section. The page goes directly from "In a nutshell" to the main content sections.

| Section | Present? | Properly Formatted? | Notes |
|---------|----------|--------------------| ------|
| Header with org, purpose, date | | | |
| Publication note | | | |
| In a nutshell (prose, NOT table) | | | |
| NO Summary section (should not exist) | | | Should be absent |
| The organization | | | |
| The intervention | | | |
| Does [intervention] work? | | | |
| The grant | | | |
| Budget for grant activities | | | |
| The case for the grant | | | |
| Cost-effectiveness | | | |
| Risks and reservations | | | |
| Plans for follow up | | | |
| Internal forecasts (with Resolved? column) | | | |
| Our process | | | |
| Relationship disclosures | | | |
| Sources | | | |

**Anti-redundancy check:**
- [ ] No preamble summary lists before subsections
- [ ] "In a nutshell" content not repeated verbatim in later sections
- [ ] No footnotes in "In a nutshell"

**Result:** [ ] COMPLETE / [ ] GAPS FOUND

---

## Audit 7: Style Guide Compliance

**Purpose:** Check adherence to GiveWell style guide.

| Check | Pass/Fail | Issues Found |
|-------|-----------|--------------|
| American English spelling | | |
| Serial (Oxford) commas | | |
| Sentence-case headers | | |
| Number formatting (1-10 spelled, 11+ numerals) | | |
| Percentage formatting (numerals + %) | | |
| "Program participants" not "beneficiaries" | | |
| Organization names singular | | |
| Required disclaimers present | | |
| Footnote format correct | | |
| "More" links where appropriate | | |

**Result:** [ ] COMPLIANT / [ ] FIXES NEEDED

---

## Audit 8: Legibility Check

**Purpose:** Verify the draft meets legibility guidance standards.

| Criterion | Met? | Evidence/Notes |
|-----------|------|----------------|
| Reader can understand what grant does from summary | | |
| Intuitive CE walkthrough present | | |
| Simple CEA elements included (if applicable) | | |
| Outside-the-model considerations explicit | | |
| Specific, falsifiable claims (not vague) | | |
| Uncertainty levels explained | | |
| "More" links to detailed sections | | |
| Key assumptions stated | | |

**Result:** [ ] LEGIBLE / [ ] IMPROVEMENTS NEEDED

---

## Audit 9: Comparison Audit

**Purpose:** Compare the draft against similar published grant pages to calibrate quality, length, and depth.

**IMPORTANT:** The template in `context/[TEMPLATE] Grant Page for [grant].md` is the authoritative source for formatting rules. If example pages use different formatting (e.g., tables for "In a nutshell"), follow the template, not the examples. Example pages may have been published before current formatting standards were established.

### 9.1 Select Comparison Pages

List the example pages you're comparing against:
- **Comparison 1:** [Page name] - Selected because [reason: similar grant size/type/intervention]
- **Comparison 2:** [Page name] - Selected because [reason]

### 9.2 Length Calibration

| Metric | Draft | Comparison 1 | Comparison 2 | Assessment |
|--------|-------|--------------|--------------|------------|
| Total word count | | | | |
| In a nutshell length | | | | |
| Case for grant length | | | | |
| Risks section length | | | | |
| Number of footnotes | | | | |

**Assessment:** Is the draft appropriately sized for this grant type?
- [ ] Appropriately sized
- [ ] Too long (flag sections to condense)
- [ ] Too short (flag sections needing expansion)

### 9.3 Structure Comparison

| Element | Draft Has? | Comparison 1 Has? | Comparison 2 Has? | Gap? |
|---------|------------|-------------------|-------------------|------|
| Cost-effectiveness table | | | | |
| Confidence intervals/ranges | | | | |
| Budget breakdown table | | | | |
| Internal forecasts table | | | | |
| "More" links in summary | | | | |
| Section sub-headers | | | | |

### 9.4 Depth Calibration

For key sections, compare the level of detail:

**In a Nutshell:**
- Draft approach: [describe]
- Comparison approach: [describe]
- Assessment: [ ] Appropriate / [ ] Adjust

**Cost-Effectiveness Section:**
- Draft approach: [describe - table vs prose, level of parameter detail]
- Comparison approach: [describe]
- Assessment: [ ] Appropriate / [ ] Adjust

**Risks and Reservations:**
- Draft: [number of risks, level of detail each]
- Comparison: [number of risks, level of detail each]
- Assessment: [ ] Appropriate / [ ] Adjust

### 9.5 Tone and Voice Check

Read a paragraph from the draft and a comparable paragraph from the example. Do they match in:
- [ ] Formality level
- [ ] Use of "we" voice
- [ ] Directness vs hedging
- [ ] Technical detail level

**Discrepancies noted:** [List any tone mismatches]

### 9.6 Comparison Summary

| Check | Pass/Fail |
|-------|-----------|
| Length appropriate for grant type | |
| Structure matches comparable pages | |
| Depth calibrated correctly | |
| Tone consistent with GiveWell voice | |

**Result:** [ ] CALIBRATED / [ ] ADJUSTMENTS NEEDED

If adjustments needed, list specific changes:
1. [Adjustment 1]
2. [Adjustment 2]

---

## Audit 10: Link Validation

**Purpose:** Verify all internal "(more)" links resolve to actual sections.

Scan the draft for all `([more](...))` links:

| # | Link Text | Target Anchor | Section Exists? | Pass/Fail |
|---|-----------|---------------|-----------------|-----------|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |

**Rules:**
- Every `([more](#...))` link must point to an existing section header
- No `([more](undefined))` links allowed
- No `[FLAG: LINK NEEDED]` markers should remain (must be resolved)
- Anchor format should be: lowercase, hyphens for spaces

**Common issues to check:**
- [ ] No `undefined` in any link targets
- [ ] No unresolved `[FLAG: LINK NEEDED]` markers
- [ ] All anchors match actual section headers

**Result:** [ ] ALL LINKS VALID / [ ] BROKEN LINKS FOUND

If broken links found, list corrections:
1. [Link location]: [Current target] → [Correct target]

---

## Overall QC Summary

| Audit | Status |
|-------|--------|
| 1. Numerics | |
| 2. Vagueness | |
| 3. Footnotes | |
| 4. Sensitivity | |
| 5. Preservation | |
| 6. Template | |
| 7. Style Guide | |
| 8. Legibility | |
| 9. Comparison | |
| 10. Link Validation | |

**BLOCKERS:** [List any blockers that prevent finalization]

**CALIBRATION ADJUSTMENTS:** [List any length/depth/structure adjustments from comparison audit]

**OVERALL STATUS:** [ ] READY FOR STAGE 5 / [ ] FIXES REQUIRED

---

## Output Location

Save your QC audit to: `output/[grant-name]/4-qc-audit.md`
