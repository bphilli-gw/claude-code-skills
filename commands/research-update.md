# Research Update

Generate a research update report for a GiveWell intervention area.

**Argument:** $ARGUMENTS (research area name, e.g., "bednets", "smc", "cmam")

---

## Workflow

```
Phase 1:  literature-search  -->  relevance-score      [Paper Discovery]
Phase 2:  report-writer      -->  report-reviewer loop  [Report Generation]
```

### Phase 1: Paper Discovery

1. **Literature Search** (uses `literature-search` skill)
   - Use the research area's standard queries from `core/research_areas.py`
   - Search Semantic Scholar for papers published in the last 30-60 days (or as specified)
   - Cast a wide net: use multiple query variations for the area
   - Collect up to 50 papers

2. **Relevance Scoring** (uses `relevance-score` skill)
   - Score all papers for CEA relevance (0-100)
   - Filter to papers scoring 60+
   - Sort by relevance score descending
   - Keep top 20 for analysis

3. **Citation Deduplication**
   - Load the corresponding intervention report from `reference/intervention-reports/`
   - Check each paper against existing citations (first-author surname + year)
   - Exclude already-cited papers (note count in methods section)

### Phase 2: Report Generation (Write-Review-Revise Loop)

1. **Write** the report using the `report-writer` skill
   - Top 5 papers get detailed analysis
   - Papers 6-20 get brief summaries
   - Emphasize parameter impact: what would change in the CEA?
   - Write in GiveWell legible style

2. **Review Loop** (uses `review-loop` + `report-reviewer` skills)
   - Follow the write-review-revise protocol
   - Max 2 iterations (lower stakes than QEA/BOTEC)

3. Present the final report to the user with:
   - Bottom line: do any papers change GiveWell's view?
   - Count of papers found vs. analyzed
   - Any papers that warrant deeper investigation

---

## Research Area Mapping

| Area | Queries | Intervention Report |
|------|---------|-------------------|
| bednets | ITN, LLIN, insecticide resistance, net distribution | `Updated nets intervention report 2025 v2.md` |
| smc | Seasonal malaria chemoprevention, SPAQ, IPT | `(Dec 2024 Update) SMC intervention report.md` |
| cmam | Acute malnutrition, RUTF, therapeutic feeding | `Community-based management of acute malnutrition.md` |

For the full list of areas and queries, see `core/research_areas.py`.

## Python Module (Alternative)

For fully automated report generation with storage integration:
```bash
python report_generator.py --area [area] --days 30 --min-score 70
```

---

## Output

Save to: `output/reports/[area]_update_[date].md`
