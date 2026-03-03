# Report Writer

Generate a research update report comparing recent papers against an existing GiveWell intervention report.

## When This Skill Applies

You have a set of scored/filtered papers from a literature search and need to produce a structured research update for a GiveWell research area.

## Inputs

- Research area (e.g., "bednets", "smc", "cmam")
- Filtered papers with relevance scores (from literature-search + relevance-score skills)
- Corresponding intervention report from `reference/intervention-reports/`

## Output

A markdown report saved to: `output/reports/[area]_update_[date].md`

---

## Report Structure

```markdown
# [Research Area] Research Update — [Date]

## Bottom Line

[1-2 sentences: Do these papers change GiveWell's view on this intervention?
If so, how? If not, why not?]

## Methods

- Search strategy: [queries used, databases searched, date range]
- Papers found: [N total]
- Papers after filtering (score >= [threshold]): [N]
- Papers already cited in intervention report: [N excluded]
- Papers analyzed in detail: [N]

## Key Findings

[3-5 bullet points summarizing the most important takeaways across all papers.
Each should reference specific papers and state the implication for CEA.]

## Detailed Analysis (Top 5 Papers)

### [Paper 1 Title] (Author et al., Year)

**Bottom line:** [What this paper means for GiveWell's estimate]

**Why I think this:** [Key findings with effect sizes and CIs]

**How I could be wrong:** [Limitations, generalizability concerns]

**Parameter impact:** [Which specific CEA parameter could change, and by how much]

[Repeat for papers 2-5]

## Brief Summaries (Papers 6-N)

| # | Paper | Key Finding | CEA Relevance |
|---|-------|-------------|---------------|
| 6 | Author (Year) | [1 sentence] | [parameter affected] |

## References

[Full citations with DOIs/links]
```

---

## Writing Style

Follow GiveWell legibility standards (see `reference/review-guidance/Legibility guidance for Claude (Feb 26) (1).md`):

- **Bottom-line first** in every section
- **First person**: "I think..." not "It can be concluded that..."
- **Specific numbers**: Effect sizes with CIs, sample sizes, p-values
- **Honest uncertainty**: Distinguish strong evidence from speculation
- **No banned phrases**: "research suggests", "studies indicate", "evidence shows"

## Citation Deduplication

Before analyzing papers, check if each paper is already cited in the intervention report. A paper is "already cited" if its first-author surname + publication year appear together in the report text. Exclude already-cited papers from detailed analysis (note them in Methods).

## Intervention Report Mapping

| Area | Report File |
|------|------------|
| bednets | `reference/intervention-reports/Updated nets intervention report 2025 v2.md` |
| smc | `reference/intervention-reports/(Dec 2024 Update) SMC intervention report.md` |
| cmam | `reference/intervention-reports/Community-based management of acute malnutrition.md` |

Read the intervention report's summary section (first ~50KB) to understand the current state of evidence before analyzing new papers.

## Python Module (Optional)

For programmatic report generation with storage integration:
```bash
python report_generator.py --area [area] --days [N] --min-score [threshold]
```
