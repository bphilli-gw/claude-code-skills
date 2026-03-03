# Review Critic

Evaluate the quality of an AI-generated peer review against GiveWell standards.

## When This Skill Applies

You are critiquing a peer review as part of the write-review-revise loop protocol (see `review-loop` skill). The review was produced by the `peer-review-writer` skill.

## Reviewer Stance

You are evaluating whether this review would be useful to the document's author. A bad review is worse than no review — it wastes the author's time on false issues or gives false confidence by missing real problems.

---

## Checklist (8 Dimensions)

| # | Criterion | What to Check |
|---|-----------|---------------|
| 1 | **Calibration** | Does the review match real GiveWell review tone and depth? Compare to examples in `reference/review-guidance/`. Is it too verbose? Too vague? Does it take a stand or hedge everything? |
| 2 | **Research effort** | Did the reviewer actually investigate, or just say "I'd want to see X"? A good reviewer checks what they can check. Flag cases where the reviewer deferred when they could have verified. Did the reviewer engage with decision questions (should we fund now vs investigate more), or only raise analytical concerns? |
| 3 | **False alarm check** | Are literature spot-check citation flags likely false positives? Semantic Scholar doesn't index everything. A "not found" result doesn't mean the paper doesn't exist. Flag overconfident "this citation appears fabricated" claims. |
| 4 | **Priority ordering** | Are the cruxes genuinely the most decision-relevant issues? Would a GiveWell program officer agree these are the top concerns? Flag cases where a nitpick is elevated to a crux or a critical issue is buried in lower-priority. |
| 5 | **Cross-reference quality** | If the review covers multiple related documents, does it compare across them? Flag missed inconsistencies or shared weaknesses. |
| 6 | **Practical questions** | Does the review raise process, implementation, and scalability questions? Not just methodology critiques but "how would this work in practice?" |
| 7 | **Originality** | Does the review surface NEW uncertainties and concerns, or does it just restate what the document already flags? A review that mostly echoes the document's own limitations section is not useful. The reviewer should be adding value by identifying blind spots, not summarizing known unknowns. |
| 8 | **Citation quality** | Does the review cite specific papers inline when making claims? Are factual assertions supported by named sources (author, year, title), or are they unsourced? Claims like "the literature suggests" or "evidence shows" without a specific citation are failures. |

---

## Mandatory Verification Steps

### V1: Calibration Test
Read the first crux/high-priority feedback item. Compare it to the example reviews:
- `reference/review-guidance/JM Review Notes - CHAI RDT_ACT in private sector (1).md` — a short, sharp, opinionated review
- `reference/review-guidance/Fortify Health open market grant renewal investigation (1).md` — a thorough deep-dive

Is the review under critique closer to these examples, or is it generic/verbose/hedging?

### V2: Research Effort Audit
Count how many times the review says "I'd want to check..." or "it would be worth investigating..." For each, ask: could the reviewer have actually checked this with available tools (literature search, calculation verification)? If yes, that's a missed research opportunity.

Also check: does the review answer the decision questions (fund now vs investigate vs deprioritize), or does it only flag analytical concerns without taking a position on next steps?

### V3: False Alarm Scan
If the review includes a literature research section, check each citation flag:
- "Not found in Semantic Scholar" — this is common for older papers, working papers, and non-English publications. Is the reviewer appropriately hedging?
- "This citation may be fabricated" — very serious claim. Is there strong evidence, or just a search failure?

### V4: Priority Ranking Test
List the cruxes/high-priority items. For each, ask: "If the author only addresses one thing, is this the right one?" and "Would this actually change the funding decision?" If the most impactful issue is in the lower-priority section, FAIL criterion #4.

### V5: Originality Test
Read the document under review's own "key uncertainties," "limitations," or "areas for further research" section. Then read the review's cruxes/high-priority feedback. Count how many of the review's crux items are simply restating the document's own acknowledged uncertainties.

- If **more than 1 out of 5** crux items is a restatement of a documented uncertainty without adding new analysis or a contrary position: **FAIL criterion #7**.
- A review item that AGREES with a documented uncertainty but adds new evidence, a specific parameter estimate, or a concrete recommendation is NOT a restatement — that's original contribution.

### V6: Citation Audit
Scan the review's crux items for factual claims. For each claim, check:
- Is it cited to a specific paper (author, year, title)? Good.
- Is it cited to a specific section of the document under review? Good.
- Is it backed by a calculation the reviewer shows? Good.
- Is it unsourced ("studies show", "evidence suggests", "the literature indicates")? **Flag as citation failure.**

If more than half of factual claims in the crux section are unsourced: **FAIL criterion #8**.

---

## Output Format

```markdown
## REVIEW CRITIQUE

**Review:** [filename]
**Overall Assessment:** Good / Needs revision / Significant gaps

### Strengths
[2-3 things the review does well]

### Issues to Fix
[Each: specific issue → specific fix]

1. **[Issue]**: [What's wrong] → [What to change]

### Missing Research
[Feasible analysis the reviewer skipped — things they could have checked but didn't]

### Cross-Reference Gaps
[If multiple reviews: what connections were missed?]

### Bottom Line
[Single most important improvement the reviewer should make]
```

When used as part of the review-loop protocol, map this output to the standard verdict format:
- "Good" → APPROVED
- "Needs revision" or "Significant gaps" → REVISE, with Issues to Fix as blocking issues

---

## Python Module (Optional)

For programmatic review critique:
```bash
python -m review.review_critic review.md --original document.md
python -m review.review_critic reports/reviews/peer_review_*.md --originals "reference/intervention-reports/bundled-inputs/*.md"
```
