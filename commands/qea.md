# QEA (Quick Evidence Assessment)

Perform a QEA on the specified intervention or study.

**Argument:** $ARGUMENTS (URL to primary study, or intervention name)

---

## Why This Matters

These QEAs help GiveWell direct millions of dollars to some of the world's most vulnerable populations. An inaccurate analysis could mean funding flows to less effective interventions, costing lives. **Do not take shortcuts. Accuracy matters more than speed.**

---

## Workflow

This workflow composes the following skills in sequence:

```
Phase 1:  literature-search  -->  split-pdf (x N)     [Evidence Gathering]
Phase 2:  botec-writer       -->  botec-reviewer loop  [BOTEC Construction]
Phase 3:  qea-writer         -->  qea-reviewer loop    [QEA Document]
```

### Phase 1: Evidence Gathering

1. **Literature Search** (uses `literature-search` skill)
   - Search Semantic Scholar for the intervention name + related terms
   - Search for existing meta-analyses, systematic reviews, and RCTs
   - Search for cost data and implementation evidence
   - Identify the 3-5 most important papers

2. **Paper Reading** (uses `split-pdf` skill)
   - For the 1-2 most critical papers (usually the primary RCT and best meta-analysis), use the `split-pdf` skill to read them in detail
   - Extract: effect sizes with CIs, sample sizes, study design, cost data, limitations
   - For other papers, read abstracts and key findings only

3. **BOTEC-First Triage**
   - After reading the abstract of the primary study, build a rough mental model:
     - What's the likely cost per beneficiary? (benchmark from similar GiveWell programs)
     - What's the likely effect size?
     - Is this plausibly >8x cash? If clearly not, note this early.
   - This triage determines how deep to go in evidence gathering

### Phase 2: BOTEC Construction (Write-Review-Revise Loop)

1. **Write** the BOTEC using the `botec-writer` skill
   - Follow the 5-question CEA framework
   - Use $1,000,000 benchmark
   - Document every parameter source
   - Include sensitivity analysis

2. **Review Loop** (uses `review-loop` + `botec-reviewer` skills)
   - Follow the write-review-revise protocol
   - Max 3 iterations
   - **User checkpoint after iteration 1**: Show the user the initial CE estimate and key parameters before further revision

3. Save the approved BOTEC (it will be embedded in the QEA)

### Phase 3: QEA Document (Write-Review-Revise Loop)

1. **Write** the QEA using the `qea-writer` skill
   - Incorporate the approved BOTEC
   - Structure per the QEA template
   - Answer the core question: Does this program seem cost-effective? Should GiveWell pursue further investigation?

2. **Review Loop** (uses `review-loop` + `qea-reviewer` skills)
   - Follow the write-review-revise protocol
   - Max 3 iterations
   - **User checkpoint after approval**: Show final bottom line and ask if user wants to review

3. Save to: `output/qeas/[intervention-name]-QEA.md`

---

## Critical Requirements (Non-Negotiable)

### No Fabricated Numbers
- Every numerical parameter MUST have a source
- If you cannot find a number, say "I could not find data on X" — do not guess
- When benchmarking, explicitly state what you're benchmarking from and why

### No Glossed-Over Uncertainties
- If something is uncertain, quantify the uncertainty (range, confidence level)
- If a parameter could change the bottom line significantly, flag it explicitly
- Do not hide weaknesses in the evidence

### Actually Read the Sources
- Do not summarize papers you haven't read
- Extract specific numbers with confidence intervals
- Note sample sizes, study designs, and limitations
- If you only read the abstract, say so

### Show Your Work
- Every calculation should be traceable
- Explain why you chose each parameter value
- When you make judgment calls (IV/EV adjustments), explain your reasoning

---

## Reference Documents

- QEA methodology: `reference/qea-templates/QEA guide and checklist.md`
- QEA template: `reference/qea-templates/GiveWell's QEA template - With guiding questions (Sept 2023).md`
- Legibility guidance: `reference/review-guidance/Legibility guidance for Claude (Feb 26) (1).md`
- BOTEC calibration: `cost_effectiveness/smc_extension_botec.py`
- Existing QEAs: `output/qeas/`

---

## Output

Save the QEA to: `output/qeas/[intervention-name]-QEA.md`
