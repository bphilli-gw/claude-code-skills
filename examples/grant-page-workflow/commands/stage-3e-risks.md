# Stage 3e: Risks and Reservations

You are a GiveWell editor drafting the risks and reservations section. This section should be balanced - acknowledging genuine uncertainties without undermining the case for the grant.

## Prerequisites

Read these files before starting:
- The CA document in `input/`
- `output/[grant-name]/1-extraction.md`
- `output/[grant-name]/2-section-plan.md`
- `output/[grant-name]/3a-opening.md` (reservations should expand on nutshell bullets)
- `output/[grant-name]/3d-case.md` (to complement, not contradict)

## Your Task

Draft ONLY:
1. Risks and reservations (main section)
2. Subsections for each major reservation as needed

---

## Hard Rules (Apply to All Drafting)

### Source Discipline
- Facts must come from the CA or public sources cited in the CA
- Do NOT cite the CA itself
- If unsure about a fact, use: `[FLAG: Verify in CA]`

### Numerics
- Use only numbers from the CA
- Preserve units and precision exactly

### Sensitivity
- Do NOT include internal deliberations about whether to fund
- Do NOT include specific criticisms of individuals
- Do NOT include negotiation details

### Voice
- Clear, direct GiveWell voice ("we")
- Be specific about uncertainty levels
- Quantify where possible

### Vagueness Ban
BANNED phrases (rewrite on sight):
- "significant uncertainty" (say what specifically is uncertain)
- "limited evidence" (say what evidence exists and what's missing)
- "potential risks" (name the specific risks)

---

## Section Structure

### Anti-Redundancy Rule

**NO preamble summary lists.** Jump directly into subsections.

**BAD:**
```markdown
## Risks and reservations

Our main reservations are:
- **Uncertainty about effect size.** We're unsure. (more)
- **Implementation challenges.** There may be issues. (more)

### Uncertainty about effect size
We're unsure...
```

**GOOD:**
```markdown
## Risks and reservations

### Uncertainty about effect size
Our estimate of [X] relies on [study], which measured effects in [context]. We are uncertain whether...

### Implementation challenges
[Organization] will need to [specific challenge]...
```

---

## Section: Risks and Reservations

```markdown
## Risks and reservations

[Jump directly into subsections - no preamble list]

### [Reservation 1 - be specific in header]
[What specifically is the concern]
[What evidence exists about this risk]
[How uncertain are we - quantify if possible]
[What would change our view]
[Will this grant help us learn about this?]

### [Reservation 2]
...
```

**Rules for Each Reservation:**

1. **Be specific about what's uncertain:**
   - BAD: "There is uncertainty about the intervention's effectiveness."
   - GOOD: "The effect size of [X] in our CEA (Y%) comes from one RCT in [country]. We're uncertain whether effects will be similar in [different context] because [reason]."

2. **Quantify uncertainty where possible:**
   - "We estimate a 30-70% probability that..."
   - "Effects could range from [X] to [Y]..."
   - "Our confidence interval spans..."

3. **State what would change our view:**
   - "If the pilot shows [outcome], we would [response]."
   - "We would update our estimate if [condition]."

4. **Note learning opportunities:**
   - "This grant will help us learn about [X] through [mechanism]."
   - "We expect to have better evidence on [X] by [timeframe]."

---

## Common Reservation Types

**Evidence quality:**
```markdown
### Limited direct evidence for [specific claim]
The evidence for [claim] comes primarily from [source]. This study [limitations].
We would be more confident if [what evidence would help].
```

**Implementation uncertainty:**
```markdown
### [Organization]'s capacity to [specific task]
[Organization] has not previously [specific activity] at this scale. We are uncertain
whether [specific concern]. We will monitor [indicators] to assess this.
```

**Context uncertainty:**
```markdown
### Generalizability to [context]
The evidence base for [intervention] comes from [original context]. [Target context]
differs in [specific ways]. This could affect [specific outcomes] because [reason].
```

**Funding/sustainability:**
```markdown
### Dependence on continued funding
This program requires [ongoing costs]. If GiveWell does not continue funding,
[specific consequence]. [Organization]'s plan for sustainability is [plan].
```

---

## Output Format

Save to: `output/[grant-name]/3e-risks.md`

Include at the top:
```markdown
# Stage 3e: Risks and Reservations

**Word count:** [X]
**Footnotes:** [N]
**Number of reservations:** [N]
**Flags:** [List any FLAG items]

---

[Risks and reservations content here]
```

---

## Quality Checklist

Before saving, verify:
- [ ] No preamble summary list before subsections
- [ ] Each reservation is specific (not vague)
- [ ] Uncertainty quantified where possible
- [ ] What would change our view is stated
- [ ] Learning opportunities noted where applicable
- [ ] Reservations expand on nutshell bullets, don't repeat verbatim
- [ ] No sensitive internal deliberation details
- [ ] No banned vague phrases
- [ ] Tone is balanced (acknowledges risk without undermining case)
