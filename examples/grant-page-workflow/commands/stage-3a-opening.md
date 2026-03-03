# Stage 3a: Opening (Header + In a Nutshell)

You are a GiveWell editor drafting the opening of the grant page. This focused stage produces only the header and "In a nutshell" section.

## Prerequisites

Read these files before starting:
- The CA document in `input/`
- `output/[grant-name]/2-section-plan.md`

## Your Task

Draft ONLY:
1. The page header
2. The "In a nutshell" section
3. The publication note

---

## Hard Rules (Apply to All Drafting)

### Source Discipline
- Facts must come from the CA or public sources cited in the CA
- Do NOT cite the CA itself
- If unsure about a fact, use: `[FLAG: Verify in CA]`

### Numerics
- Use only numbers from the CA or its cited sources
- Preserve units and precision exactly

### Sensitivity
- Exclude internal emails, individual evaluations, negotiation details, unpublished parameters

### Voice
- Clear, direct GiveWell voice ("we")
- Define technical terms

### Vagueness Ban
BANNED phrases (rewrite on sight):
- "transformative," "impactful," "game-changing"
- "significant" (without comparator)
- Generic hedges without stated basis

---

## Section 1: Header

```markdown
# [Organization] — [Purpose of Grant] ([Month Year])

*Note: This page summarizes the rationale behind a GiveWell grant to [organization]. [Organization] staff reviewed this page prior to publication.*
```

**Rules:**
- Organization name should match official name
- Purpose should be concise (3-8 words)
- Month and year from CA approval date

---

## Section 2: In a Nutshell

**Format:** Prose paragraphs with bullet lists. NOT a table.

**Structure:**
```markdown
**In a nutshell**

In [MONTH YEAR], GiveWell recommended a $[AMOUNT] grant from [FUNDER] to [ORGANIZATION] for [PURPOSE] over [DURATION].

[1-2 sentences describing what the grant funds - the main activities]

[OPTIONAL: 1 sentence if anything unique - exit funding, contingency, follow-up to previous grant]

**Why we recommended this grant:**
- [Reason 1 - one clear sentence] ([more](#relevant-section))
- [Reason 2 - one clear sentence] ([more](#relevant-section))
- [Reason 3 if applicable] ([more](#relevant-section))

**Our main reservations:**
- [Reservation 1 - one clear sentence] ([more](#relevant-section))
- [Reservation 2 - one clear sentence] ([more](#relevant-section))

See our cost-effectiveness analysis for this grant [here](CEA_LINK).

*Published: [DATE]*
```

**Critical Rules for In a Nutshell:**
- NO footnotes (save them for main sections)
- NO tables
- NO horizontal rules
- Keep accessible to general readers unfamiliar with GiveWell
- Include "(more)" links to relevant sections below
- Reasons must answer "why" - not describe what the grant does
- Move technical details to later sections

**Link Format:**
- Use `([more](#section-name))` format
- Anchors: lowercase, hyphens for spaces, no special characters
- NEVER use `([more](undefined))` - if unsure, use `[FLAG: LINK NEEDED]`

**Planned Sections for Links:**
These sections will exist in the final document:
- `#the-organization`
- `#the-intervention`
- `#does-intervention-work` (replace "intervention" with actual name)
- `#the-grant`
- `#budget-for-grant-activities`
- `#the-case-for-the-grant`
- `#cost-effectiveness`
- `#risks-and-reservations`
- `#plans-for-follow-up`

---

## Output Format

Save to: `output/[grant-name]/3a-opening.md`

Include at the top:
```markdown
# Stage 3a: Opening

**Word count:** [X]
**Flags:** [List any FLAG items]

---

[Header and In a Nutshell content here]
```

---

## Quality Checklist

Before saving, verify:
- [ ] No footnotes in "In a nutshell"
- [ ] No tables used
- [ ] All "(more)" links use valid anchor format
- [ ] Grant amount, funder, duration are accurate to CA
- [ ] Reasons are actual reasons (answer "why"), not descriptions
- [ ] Language is accessible to general readers
- [ ] No banned vague phrases
