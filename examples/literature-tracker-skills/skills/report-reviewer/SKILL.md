# Report Reviewer

Verify a research update report for accuracy, completeness, and analytical quality.

## When This Skill Applies

You are reviewing a research update report as part of the write-review-revise loop protocol (see `review-loop` skill). The report was produced by the `report-writer` skill.

## Reviewer Stance

You are a GiveWell program officer who will use this report to decide whether to update an intervention's cost-effectiveness estimate. Missed papers or misrepresented findings could lead to bad decisions.

---

## Checklist

| # | Criterion | What to Check |
|---|-----------|---------------|
| 1 | **Bottom-line presence** | Report starts with a clear bottom line about whether these papers change GiveWell's view. Not "these are interesting papers" but "these papers [do/don't] change our estimate because [reason]." |
| 2 | **Methods transparency** | Search strategy documented: queries used, databases, date range, filtering criteria, number excluded. |
| 3 | **Paper-report alignment** | For each top-5 paper, the "parameter impact" claim references a parameter that actually exists in the intervention report. FAIL if a claimed parameter doesn't match. |
| 4 | **Citation accuracy** | Spot-check 2 paper summaries. Verify the stated findings are consistent with the paper's title and abstract. Key findings should not be misrepresented. |
| 5 | **Citation deduplication** | Papers already cited in the intervention report are excluded from analysis (or explicitly noted). |
| 6 | **Confidence calibration** | Single observational studies don't produce "high confidence" claims. Meta-analyses of RCTs warrant higher confidence. Check 2-3 claims for appropriate confidence. |
| 7 | **Legibility** | Written in first person, bottom-line first per section, no banned phrases ("research suggests", "evidence shows"). |
| 8 | **Completeness** | All sections present: bottom line, methods, key findings, detailed analysis, brief summaries, references. |

---

## Mandatory Verification Steps

### V1: Bottom Line Test
Read only the "Bottom Line" section. Does it answer: "Should we update our cost-effectiveness estimate?" If it's vague or hedging without specifics, FAIL criterion #1.

### V2: Paper-Report Alignment Check
For 2 of the top-5 papers, verify the "parameter impact" claim. Check: does the intervention report actually contain this parameter? Is the direction of impact stated? Would the finding actually change the parameter in the stated direction?

### V3: Citation Spot-Check
Pick 2 paper summaries. Read the paper's title and abstract metadata (from the search results). Verify the report's summary is consistent — key findings aren't overstated, study type is correct, effect sizes are in the right ballpark.

### V4: Confidence Calibration Check
Find 2-3 confidence claims in the report. For each, check:
- Is the underlying evidence described (study type, sample size)?
- Is the confidence level appropriate for that evidence quality?
- Flag any case where a single small study is treated as definitive

---

## Output Format

Follow the standard reviewer verdict format from the `review-loop` skill.
