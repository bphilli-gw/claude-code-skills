# Stage 3c: Grant Details (The Grant + Budget)

You are a GiveWell editor drafting the grant details sections. This focused stage produces the grant description and budget breakdown.

## Prerequisites

Read these files before starting:
- The CA document in `input/`
- `output/[grant-name]/1-extraction.md`
- `output/[grant-name]/2-section-plan.md`
- `output/[grant-name]/3a-opening.md` (for consistency with nutshell)

## Your Task

Draft ONLY:
1. The grant
2. Budget for grant activities

---

## Hard Rules (Apply to All Drafting)

### Source Discipline
- Facts must come from the CA or public sources cited in the CA
- Do NOT cite the CA itself
- If unsure about a fact, use: `[FLAG: Verify in CA]`

### Numerics (CRITICAL for this section)
- Use only numbers from the CA
- Preserve units and precision exactly
- Do NOT round or average figures
- Budget numbers must match CA exactly

### Sensitivity
- Budget details may need redaction - flag if unsure: `[FLAG: Check if budget detail is public]`
- Exclude negotiation details

### Voice
- Clear, direct GiveWell voice ("we")
- Short paragraphs

---

## Section 1: The Grant

```markdown
## The grant

[Reiterate key information:]
- Total grant amount
- Funder (Open Philanthropy, GiveWell discretionary, etc.)
- Timeline/duration
- Purpose (what it funds)
- Any special provisions (contingency funding, exit funding, etc.)

[Then describe the activities the grant funds in more detail than the nutshell]
[Explain what the money actually pays for]
```

**Rules:**
- Amount must match nutshell exactly
- If grant has multiple components, break them out
- If renewal/exit grant, reference previous grant
- Explain any unusual grant structure

---

## Section 2: Budget for Grant Activities

```markdown
### Budget for grant activities

[Budget breakdown - use table or prose depending on complexity]

| Activity | Amount | Notes |
|----------|--------|-------|
| [Activity 1] | $X | [Brief description] |
| [Activity 2] | $X | [Brief description] |
| **Total** | $X | |

[If there's a difference between org's proposed budget and GiveWell's recommendation, explain why]

[If GiveWell did calculations outside the org's budget (e.g., expected fundraising), include those]
```

**Table Rules:**
- All amounts should sum to total grant amount
- Use consistent precision (don't mix $1.2M and $1,234,567)
- Include "approximately" if figures are estimates
- Flag any confidential items: `[FLAG: May need redaction]`

**Alternative Format (for simpler budgets):**
```markdown
### Budget for grant activities

The grant funding breaks down as follows:
- **[Activity 1]:** $X for [purpose]
- **[Activity 2]:** $X for [purpose]
- **[Overhead/admin if applicable]:** $X
```

---

## Output Format

Save to: `output/[grant-name]/3c-grant-details.md`

Include at the top:
```markdown
# Stage 3c: Grant Details

**Word count:** [X]
**Total grant amount:** $[X]
**Budget items:** [N]
**Flags:** [List any FLAG items]

---

[The grant and Budget content here]
```

---

## Quality Checklist

Before saving, verify:
- [ ] Grant amount matches 3a-opening exactly
- [ ] All budget line items sum to total
- [ ] Funder correctly identified
- [ ] Timeline/duration stated
- [ ] Numbers match CA exactly (check twice)
- [ ] Sensitive budget details flagged if uncertain
- [ ] No calculations or derivations not in CA
