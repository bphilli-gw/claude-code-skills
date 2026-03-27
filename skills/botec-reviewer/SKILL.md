# BOTEC Reviewer

Verify a BOTEC cost-effectiveness calculation for accuracy, sourcing, and plausibility.

## When This Skill Applies

You are reviewing a BOTEC as part of the write-review-revise loop protocol (see `review-loop` skill). The BOTEC was produced by the `botec-writer` skill.

## Reviewer Stance

You are NOT the author. You are a skeptical GiveWell colleague who just received this BOTEC for sign-off. Your reputation depends on catching errors that could misdirect millions in funding. A BOTEC with wrong numbers is worse than no BOTEC at all.

Before writing your verdict, ask yourself:
1. "Am I approving this because it's actually good, or because I wrote it and don't want to redo work?"
2. "If the cost estimate is off by 2x, does the bottom line flip?"
3. "Would an experienced GiveWell researcher find problems I'm missing?"

---

## Checklist

Evaluate each criterion. Record PASS/FAIL with specific evidence in the verdict table.

| # | Criterion | What to Check |
|---|-----------|---------------|
| 1 | **Arithmetic consistency** | Re-derive the final CE multiple from the stated parameters. Must match within 5%. |
| 2 | **Source documentation** | Every parameter >1% CE impact has author/year/table/page citation. No "literature suggests" or "GBD data shows" without specifics. |
| 3 | **Counterfactual coverage** | Explicitly stated and non-zero (or justified if zero). Not silently assumed to be 0%. |
| 4 | **Peer comparison** | CE estimate compared to at least one existing GiveWell-funded intervention. The comparison should make intuitive sense. |
| 5 | **Sensitivity analysis** | Present with at least 3 scenarios. Pessimistic scenario uses pessimistic values for ALL key parameters simultaneously (not one-at-a-time). |
| 6 | **IV/EV adjustments** | Direction explained with reasoning, not just "90% IV adjustment." Why 90% and not 80%? |
| 7 | **Parameter plausibility** | No parameter >2x different from peer interventions without explicit explanation. Cost estimates not taken from trial settings without implementation markup. |
| 8 | **NNT/cost sanity check** | Number needed to treat and cost-per-outcome fall within plausible ranges for this intervention type. |
| 9 | **GiveWell constants** | Uses moral weight = 116 for under-5 life, cash benchmark = 0.0033545. |
| 10 | **Standard table format** | Parameter table present with Parameter / Value / Source / Confidence columns. |

---

## Mandatory Verification Steps

Complete ALL of these before issuing a verdict. Record results in the checklist.

### V1: Arithmetic Reconstruction
Re-derive the final CE multiple from scratch using the parameters stated in the document. Show your calculation. If your result differs from the document's by >5%, FAIL criterion #1.

### V2: Source Spot-Check
Pick the 2 parameters with highest sensitivity (i.e., changing them by 20% changes the CE most). For each:
- Read the cited source if available and verify the number matches
- If the source is not available, flag as UNVERIFIED (not an automatic FAIL, but note it)

### V3: Counterfactual Coverage Check
Verify the document explicitly states a counterfactual coverage percentage. If it's 0%, there must be a justification (e.g., "this is a novel intervention with no existing delivery"). If missing or unjustified, FAIL criterion #3.

### V4: Peer Intervention Comparison
Check that the document compares its CE estimate to at least one GiveWell top charity. If the new intervention claims to be >3x more cost-effective than the comparator, apply extra scrutiny — this is unusual and the burden of proof is high.

### V5: Pessimistic Scenario Validation
Check the "very conservative" or "pessimistic" scenario. It should use pessimistic values for ALL key parameters simultaneously. If the pessimistic scenario still clears 10x cash, flag as "possibly overoptimistic" — this suggests the analysis may have systematic upward bias.

---

## Calibration Reference

Before issuing your verdict, compare the parameter documentation quality to:
`cost_effectiveness/smc_extension_botec.py`

This file demonstrates the standard for source documentation: each parameter has a comment block with SOURCE, QUERY, ACCESSED date, RAW VALUE, ADJUSTMENT rationale, CONFIDENCE level, and SENSITIVITY range. If the document under review has less detailed sourcing than this example, that is a FAIL on criterion #2.

---

## Anti-Patterns to Flag

- "Estimated from literature" without specifying which literature
- Effect sizes >50% relative risk reduction without extra scrutiny
- Cost estimates from trial settings without inflation for real-world implementation (add 25-50% buffer)
- Optimistic assumptions on all parameters simultaneously
- Missing funging/leverage discussion
- Assuming 100% adherence or coverage
- Using a single study for a critical parameter when meta-analyses exist

---

## Output Format

Follow the standard reviewer verdict format from the `review-loop` skill.
