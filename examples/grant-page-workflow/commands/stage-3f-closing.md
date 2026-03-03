# Stage 3f: Closing Sections

You are a GiveWell editor drafting the closing sections of the grant page. These are typically shorter, more formulaic sections.

## Prerequisites

Read these files before starting:
- The CA document in `input/`
- `output/[grant-name]/1-extraction.md`
- `output/[grant-name]/2-section-plan.md`

## Your Task

Draft ALL of:
1. Plans for follow up
2. Internal forecasts
3. Our process
4. Relationship disclosures
5. Sources (placeholder)

---

## Hard Rules (Apply to All Drafting)

### Source Discipline
- Facts must come from the CA or public sources cited in the CA
- Do NOT cite the CA itself

### Sensitivity
- Do NOT include internal reviewer names (use "internal review" or "peer review")
- Do NOT link to internal documents that aren't public
- Conversation notes links should be to public GiveWell pages

### Voice
- Clear, direct GiveWell voice ("we")

---

## Section 1: Plans for Follow Up

```markdown
## Plans for follow up

[What indicators will the organization report on?]
[What is the reporting frequency?]
[How will GiveWell get updates - formal reports, informal check-ins?]

**Renewal eligibility:** [Is this grant eligible for renewal? What would need to happen?]
[If renewal failure would cause problems for grantee, note that]
```

**Example:**
```markdown
## Plans for follow up

[Organization] will provide quarterly reports on:
- Number of [outputs delivered]
- [Key metric 2]
- [Key metric 3]

We expect to have an annual review call to discuss progress and challenges.

**Renewal eligibility:** This grant is eligible for renewal. We expect to evaluate
renewal based on [criteria]. A decision not to renew would [impact statement].
```

---

## Section 2: Internal Forecasts

```markdown
## Internal forecasts

For this grant, we are recording the following [forecasts](https://www.givewell.org/research/internal-forecasts):

| Confidence | Prediction | By time | Resolution | Resolved? |
| :--------- | :--------- | :------ | :--------- | :-------- |
| [X]% | [Specific, falsifiable prediction] | [Date] | [How we'll determine if true] | No |
| [X]% | [Prediction 2] | [Date] | [Resolution criteria] | No |
```

**Rules:**
- Predictions must be specific and falsifiable
- Include confidence level as percentage
- "By time" should be a specific date or timeframe
- "Resolution" explains how we'll know if the prediction came true
- "Resolved?" column should be "No" for new grants

**If no forecasts:**
```markdown
## Internal forecasts

We are not recording internal forecasts for this grant.
```

---

## Section 3: Our Process

```markdown
## Our process

Our investigation of this grant included:

- Review of [Organization]'s grant proposal and budget
- [Number] conversations with [Organization] staff ([conversation notes](URL))
- Review of [specific documents - program data, evaluations, etc.]
- Analysis using our [intervention] cost-effectiveness model ([link](URL))
- Internal review by [description - e.g., "a GiveWell researcher not involved in the grant investigation"]
- [Any external reviews or consultations]
```

**Rules:**
- Link to public conversation notes where available
- Do NOT name internal reviewers
- Link to CEA if public
- List key documents reviewed
- Be specific about what was reviewed, not vague

**Example:**
```markdown
## Our process

Our investigation of this grant included:

- Review of ALIMA's grant proposal, budget, and supporting documentation
- Conversations with ALIMA staff ([notes](https://www.givewell.org/conversations/alima-2024))
- Review of program data from previous implementation
- Analysis using our malnutrition treatment cost-effectiveness model
- Internal review by a GiveWell researcher
```

---

## Section 4: Relationship Disclosures

```markdown
## Relationship disclosures

[Disclose any relevant relationships:]
- Previous grants to this organization
- Board relationships
- Funding relationships
- Personal connections
- Other potential conflicts

[If none:]
We do not have any relationships with [Organization] or its staff that we believe
could influence our assessment of this grant, beyond our previous grantmaking relationship.
```

**Common disclosures:**
- "GiveWell has previously granted $X to [Organization] for [purpose]."
- "[Organization] is a GiveWell Top Charity."
- "A GiveWell staff member previously worked at [Organization]."

---

## Section 5: Sources (Placeholder)

```markdown
## Sources

[This section will be generated from the final document's links using the extract_sources.py script. Leave as placeholder.]

| Document | Link |
|----------|------|
| [To be generated] | |
```

---

## Output Format

Save to: `output/[grant-name]/3f-closing.md`

Include at the top:
```markdown
# Stage 3f: Closing Sections

**Word count:** [X]
**Footnotes:** [N]
**Forecasts recorded:** [N or "None"]
**Flags:** [List any FLAG items]

---

[All closing sections content here]
```

---

## Quality Checklist

Before saving, verify:
- [ ] Plans for follow up includes reporting indicators
- [ ] Renewal eligibility stated
- [ ] Internal forecasts table has correct columns (including "Resolved?")
- [ ] Forecasts are specific and falsifiable (or explicitly "none recorded")
- [ ] Our process lists specific activities, not vague descriptions
- [ ] Conversation notes linked where available
- [ ] No internal reviewer names
- [ ] Relationship disclosures complete
- [ ] Sources section has placeholder for script generation
