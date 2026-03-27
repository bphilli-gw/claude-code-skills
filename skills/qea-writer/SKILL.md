# QEA Writer

Write a Quick Evidence Assessment document in GiveWell style.

## When This Skill Applies

You are writing a QEA report — either as part of the `/qea` workflow or standalone. The BOTEC should already be completed before writing the full QEA.

## Inputs

- Intervention name and description
- Completed BOTEC (from botec-writer)
- Evidence gathered from literature search and paper reading
- (Optional) Related GiveWell intervention reports for context

## Output

A markdown document saved to: `output/qeas/[intervention-name]-QEA.md`

---

## Writing Style

### Voice and Approach
- **First person, bottom-line first.** Start every section with what you think, then explain why.
- **Specific numbers, not vague claims.** "I estimate 0.3 deaths averted per 1000 children" not "the intervention reduces mortality."
- **Honest uncertainty.** Distinguish "I'm fairly confident (3 RCTs agree)" from "this is a rough guess (one observational study)."
- **Reasoning chains.** Show the path from evidence to conclusion so the reader can disagree with specific steps.
- **What would change your mind.** For every major claim, state what evidence would make you update.

### Banned Phrases
Never write:
- "Research suggests..." / "Studies indicate..." / "Evidence shows..."
- "Promising results" / "Significant findings" (without specifying what)
- "Further research is needed" (without saying what specific research and why it matters)
- "Cost-effective" without a number

### Confidence Tiers
- **High confidence**: "I think X is likely (3 RCTs, consistent results, large samples)"
- **Medium confidence**: "My best guess is X, but I could see it being Y (limited evidence, some inconsistency)"
- **Low confidence**: "I'm quite uncertain — X is my central estimate but the range is wide (one study, indirect evidence)"

---

## Document Structure

```markdown
# [Intervention Name] — Quick Evidence Assessment

## Summary

### Bottom Line
[CE estimate in multiples of cash. One sentence.]

### Rationale
[2-3 sentences: why you think this estimate is roughly right]

### Key Uncertainties
[3-5 most important uncertainties, each with potential impact on CE]

### Next Steps
[What you'd do with more time — specific research questions, not vague]

---

## Problem

### What is the burden?
[Quantified disease burden with GBD/WHO sources. Specific populations and geographies.]

### Who is affected?
[Target population demographics, geographic concentration]

## Program

### What is the intervention?
[Mechanism of action, delivery method, target population]

### How is it delivered?
[Implementation details: who delivers, at what scale, through what channels]

### Existing evidence of implementation
[Where has this been tried? At what scale? By whom?]

## Evidence of Effectiveness

### Direct effects
[Effect on primary outcome. IV/EV assessment for each key study.]

### Study quality assessment
[For each key study: design, sample size, effect size with CI, limitations]

### Spillover and indirect effects
[Secondary outcomes, long-term effects, externalities]

## Cost-Effectiveness

[Embed the approved BOTEC here — the full parameter table and calculation]

### Key Drivers
[Which parameters matter most for the CE estimate, with sensitivity]

### Comparison to Existing Programs
[How does this compare to GiveWell top charities?]

## Key Uncertainties and Risks

[Expanded discussion of the 3-5 uncertainties from the summary]

---

## References

[Full citations for all sources used]
```

---

## Quality Standards

Before considering the QEA complete:

- [ ] Every number has a specific source (author, year, table/page or database query)
- [ ] Effect sizes include confidence intervals where available
- [ ] IV and EV adjustments have directional reasoning
- [ ] The 3-5 biggest uncertainties are identified with potential CE impact
- [ ] Counterfactual coverage is explicitly addressed
- [ ] Bottom line is stated upfront with a specific CE multiple
- [ ] Calculations are shown and traceable
- [ ] No fabricated or guessed critical parameters
- [ ] BOTEC is embedded with full parameter table

## Reference Documents

- QEA methodology: `reference/qea-templates/QEA guide and checklist.md`
- QEA template: `reference/qea-templates/GiveWell's QEA template - With guiding questions (Sept 2023).md`
- Legibility guidance: `reference/review-guidance/Legibility guidance for Claude (Feb 26) (1).md`
- Example QEAs for calibration: `output/qeas/` (existing QEAs)
