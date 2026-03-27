# BOTEC (Back-of-the-Envelope Calculation)

Build a cost-effectiveness estimate for the specified intervention.

**Argument:** $ARGUMENTS (intervention name, study URL, or research question)

---

## Workflow

```
Phase 1:  literature-search  -->  split-pdf (x N)     [Evidence Gathering]
Phase 2:  botec-writer       -->  botec-reviewer loop  [BOTEC Construction]
```

### Phase 1: Evidence Gathering

1. **Literature Search** (uses `literature-search` skill)
   - Search for the intervention + "cost-effectiveness", "RCT", "meta-analysis"
   - Search for cost data: delivery costs, commodity costs, implementation reports
   - Identify benchmark comparator (similar GiveWell-funded program)
   - Find 2-3 key papers with effect size data

2. **Paper Reading** (uses `split-pdf` skill)
   - Read the most critical paper(s) for effect size and cost data
   - Extract: effect sizes with CIs, NNT, cost per beneficiary, coverage rates
   - Note study populations and settings (for external validity assessment)

### Phase 2: BOTEC Construction (Write-Review-Revise Loop)

1. **Write** the BOTEC using the `botec-writer` skill
   - Follow the 5-question CEA framework
   - Start with $1,000,000 benchmark donation
   - Document every parameter with specific sources
   - Include 4 scenarios: optimistic, base case, conservative, very conservative

2. **Review Loop** (uses `review-loop` + `botec-reviewer` skills)
   - Follow the write-review-revise protocol
   - Max 3 iterations
   - **User checkpoint after iteration 1**: Show the initial CE estimate, key parameters, and reviewer's concerns

3. Present the final approved BOTEC to the user with:
   - Bottom-line CE multiple (base case)
   - Range across scenarios
   - The 2-3 parameters that matter most
   - What additional evidence would most reduce uncertainty

---

## Output

Save to: `output/qeas/[intervention-name]-BOTEC.md`
