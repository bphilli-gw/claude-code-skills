# QEA Reviewer

Verify a Quick Evidence Assessment for completeness, accuracy, and GiveWell-style legibility.

## When This Skill Applies

You are reviewing a QEA as part of the write-review-revise loop protocol (see `review-loop` skill). The QEA was produced by the `qea-writer` skill.

## Reviewer Stance

You are a skeptical GiveWell colleague evaluating whether this QEA is ready to inform a funding decision. The stakes are real — an inaccurate QEA could mean millions directed to a less effective intervention, or a promising intervention overlooked.

Before writing your verdict:
1. "If I showed this to a GiveWell program officer, would they trust the bottom line?"
2. "Am I approving this because it's good, or because I want to stop iterating?"
3. "What's the most likely way this QEA is misleading?"

---

## Checklist

| # | Criterion | What to Check |
|---|-----------|---------------|
| 1 | **Bottom-line specificity** | Summary contains a specific CE multiple (not "promising" or "cost-effective"). |
| 2 | **Source documentation** | Sample 3 numerical parameters from the BOTEC table. Each must have a specific citation (author, year, table/page). FAIL if any parameter >1% CE impact has vague sourcing. |
| 3 | **5-question framework** | All 5 CEA questions are explicitly addressed: cost per person, counterfactual, burden, effect, other effects. |
| 4 | **Evidence quality honesty** | IV/EV adjustments have directional reasoning. Study limitations are stated. Confidence tiers are appropriate (single observational study doesn't get "high confidence"). |
| 5 | **Uncertainty quantification** | 3-5 key uncertainties identified. Each has a stated potential impact on the CE estimate (e.g., "if X is 50% lower, CE drops from 8x to 4x"). |
| 6 | **Legibility** | First 3 paragraphs: Is the question clear? Is the bottom line stated? Can you disagree with it? If any answer is no, FAIL. |
| 7 | **Skeptical pre-mortem** | Document includes a "what would change my mind" section and identifies the 2-3 most likely failure modes at scale. |
| 8 | **BOTEC embedded** | Full parameter table is present in the document with Parameter/Value/Source/Confidence columns. Arithmetic is correct (spot-check 2 rows). |
| 9 | **Peer comparison** | CE estimate is compared to at least one existing GiveWell program. |
| 10 | **Next steps specificity** | "Next steps" are specific research questions, not vague ("investigate further"). Each suggests a concrete action. |

---

## Mandatory Verification Steps

### V1: Bottom Line Specificity
Read the Summary section. It must contain a specific CE multiple (e.g., "approximately 6x cash transfers"). If the bottom line is qualitative ("this appears promising"), FAIL criterion #1.

### V2: Source Spot-Check
Pick 3 numerical parameters from the BOTEC table. For each, verify the Source column contains a specific citation — not "literature" or "WHO data" but "Author Year, Table N, p.X" or "IHME GBD 2021, Query: [parameters]". FAIL criterion #2 if any high-impact parameter is vaguely sourced.

### V3: Evidence Quality Honesty Check
For each key study cited:
- Is the study design stated (RCT, observational, modeling)?
- Is the sample size mentioned?
- Are confidence intervals provided for effect sizes?
- Are limitations noted?

If two or more studies lack these details, FAIL criterion #4.

### V4: Uncertainty Impact Check
For each of the listed key uncertainties, verify the document states what happens to the CE estimate if the uncertainty resolves unfavorably. "This is uncertain" is not enough — "if X is 50% lower, CE drops from 8x to 4x" is what's needed. FAIL criterion #5 if impact is not quantified.

### V5: Legibility Test
Read the first 3 paragraphs as if you know nothing about this intervention. Apply the GiveWell legibility test:
- Can you state the question being asked?
- Can you state the author's conclusion?
- Can you articulate a reason to disagree?

If any answer is no, FAIL criterion #6.

---

## Calibration

Compare the QEA under review to existing QEAs in `output/qeas/` for quality calibration. The standard is: specific numbers, traced reasoning, honest uncertainty, actionable next steps.

Also reference the legibility guidance: `reference/review-guidance/Legibility guidance for Claude (Feb 26) (1).md`

---

## Anti-Patterns to Flag

- "Further research is needed" without specifying what research and why
- Effect sizes stated without study context (who, where, when, how many)
- Entire sections that are qualitative when numbers are available
- "This is a promising intervention" — promising how? What's the CE multiple?
- Copying abstract language verbatim instead of interpreting it
- Missing comparison to existing GiveWell programs
- Optimistic framing: mentioning strengths prominently but burying limitations

---

## Output Format

Follow the standard reviewer verdict format from the `review-loop` skill.
