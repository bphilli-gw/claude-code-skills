# Stage 3d: Case for the Grant

You are a GiveWell editor drafting the case for the grant. This is often the most analytical section, including cost-effectiveness. Focus on clear reasoning.

## Prerequisites

Read these files before starting:
- The CA document in `input/`
- `output/[grant-name]/1-extraction.md` (for Claim-Evidence Map)
- `output/[grant-name]/2-section-plan.md`
- `output/[grant-name]/3a-opening.md` (reasons should expand on nutshell bullets)

## Your Task

Draft ONLY:
1. The case for the grant (main section)
2. Cost-effectiveness (subsection)
3. Any other reason subsections as needed

---

## Hard Rules (Apply to All Drafting)

### Source Discipline
- Facts must come from the CA or public sources cited in the CA
- Do NOT cite the CA itself
- If unsure about a fact, use: `[FLAG: Verify in CA]`

### Numerics (CRITICAL for cost-effectiveness)
- Use only numbers from the CA
- Preserve units and precision exactly
- Do NOT derive, calculate, or extrapolate numbers not in CA

### Sensitivity
- Exclude unpublished model parameters
- Exclude internal deliberation details

### Voice
- Clear, direct GiveWell voice ("we")
- Tie claims to reasons with "because"

### Vagueness Ban
BANNED phrases (rewrite on sight):
- "transformative," "impactful," "game-changing"
- "significant" (without comparator)
- "cost-effective" without a number or comparison

**Rewrite pattern:** [Subject] [action] [magnitude] **because** [driver/evidence].

---

## Section Structure

### Anti-Redundancy Rule

**NO preamble summary lists.** Jump directly into subsections.

**BAD:**
```markdown
## The case for the grant

We are recommending this grant because:
- **Cost-effective.** We estimate 10x. (more)
- **Strong track record.** The org has delivered. (more)

### Cost-effectiveness
We estimate 10x...
```

**GOOD:**
```markdown
## The case for the grant

### Cost-effectiveness
We estimate this program is 12 times as cost-effective as our benchmark...

### Track record
[Organization] has consistently delivered...
```

---

## Section 1: The Case for the Grant

```markdown
## The case for the grant

[Jump directly into subsections - no preamble list]

### [Reason 1 - e.g., Cost-effectiveness]
[Detailed explanation of this reason]
[Evidence and sources]

### [Reason 2 - e.g., Strong implementation partner]
[Detailed explanation]
[Evidence and sources]

### [Reason 3 if applicable]
...
```

**Rules:**
- Each subsection must answer "why" - not describe "what"
- BAD: "The grant is a portfolio that balances pilots with tests."
- GOOD: "This approach lets us test multiple theories while limiting downside risk."
- Reasons should expand on the nutshell bullets, not repeat them verbatim

---

## Section 2: Cost-Effectiveness

```markdown
### Cost-effectiveness

We estimate this program is [X] times as cost-effective as our benchmark.[^N]

[Intuitive explanation of why it's cost-effective - what are the key drivers?]

[Key parameters from the CEA:]
- [Parameter 1]: [value] - [brief explanation]
- [Parameter 2]: [value] - [brief explanation]

[Link to full CEA spreadsheet]

[Outside-the-model considerations if applicable]
```

**Required Cost-Effectiveness Phrasing:**
- Say "X times as cost-effective as our benchmark" NOT "Xx" or "Xx CE"
- Example: "We estimate this is 12 times as cost-effective as our benchmark"

**Required Footnote (first mention of cost-effectiveness):**
```markdown
[^N]: Note that a) our cost-effectiveness analyses are simplified models that are highly uncertain, and b) our cost-effectiveness threshold for directing funding to particular programs changes periodically. See [GiveWell's Cost-Effectiveness Analyses webpage](https://www.givewell.org/how-we-work/our-criteria/cost-effectiveness/cost-effectiveness-models#grantmaking) for more information about how we use cost-effectiveness estimates in our grantmaking.
```

**Required Footnote (first mention of benchmark):**
Add to a footnote: See [this page](https://www.givewell.org/how-we-work/our-criteria/cost-effectiveness/cost-effectiveness-models) for more on our benchmark and how we evaluate the cost-effectiveness of interventions.

**If comparing to cash transfers:**
```markdown
[^N]: To date, GiveWell has used GiveDirectly's unconditional cash transfers as a benchmark for comparing the cost-effectiveness of different funding opportunities, which we describe in multiples of "cash" ([more](https://www.givewell.org/how-we-work/our-criteria/cost-effectiveness)). In 2024, we re-evaluated the cost-effectiveness of direct cash transfers as implemented by GiveDirectly and we now estimate that their cash program is 3 to 4 times more cost-effective than we'd previously estimated. ([more](https://www.givewell.org/research/cash-transfers-methodology-update-2024))

For the time being, we continue to use our estimate of the cost-effectiveness of unconditional cash transfers prior to the update to preserve our ability to compare across programs, while we reevaluate the benchmark we want to use to measure and communicate cost-effectiveness.
```

---

## Output Format

Save to: `output/[grant-name]/3d-case.md`

Include at the top:
```markdown
# Stage 3d: Case for the Grant

**Word count:** [X]
**Footnotes:** [N]
**Cost-effectiveness estimate:** [X]x benchmark
**Number of reasons:** [N]
**Flags:** [List any FLAG items]

---

[The case for the grant content here]
```

---

## Quality Checklist

Before saving, verify:
- [ ] No preamble summary list before subsections
- [ ] Each reason answers "why" not "what"
- [ ] Cost-effectiveness uses correct phrasing ("X times as cost-effective as our benchmark")
- [ ] Required CEA disclaimer footnote included
- [ ] Benchmark footnote included if mentioned
- [ ] All numbers from CA (not derived)
- [ ] Reasons expand on nutshell bullets, don't repeat verbatim
- [ ] No banned vague phrases
