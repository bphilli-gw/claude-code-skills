# Relevance Score

Score and filter papers for relevance to GiveWell cost-effectiveness analysis.

## When This Skill Applies

You have a list of papers from a literature search and need to filter them to the most relevant ones before deeper analysis.

## Method

### Option A: Python Module (for batch scoring)

Use the project's relevance scorer for consistent, automated scoring:

```bash
python -c "
from analysis.claude_client import ClaudeClient
from analysis.relevance_scorer import RelevanceScorer
scorer = RelevanceScorer(ClaudeClient())
result = scorer.score_paper({
    'title': 'PAPER TITLE',
    'abstract': 'PAPER ABSTRACT',
}, research_area='AREA_NAME')
import json
print(json.dumps(result, indent=2))
"
```

This returns: `relevance_score` (0-100), `key_findings`, `methodology`, `cea_relevance`, `priority`.

### Option B: Manual Scoring (for interactive use)

Apply this rubric to each paper's title + abstract:

| Score Range | Criteria | Examples |
|-------------|----------|----------|
| **80-100** | Directly updates CEA parameters | RCTs with effect sizes, cost data, meta-analyses updating existing estimates |
| **60-79** | Potentially relevant to CEA | Observational studies, mechanism research, implementation evidence |
| **40-59** | Tangentially relevant | Background context, related but different interventions |
| **0-39** | Not relevant | Wrong population, wrong intervention, purely theoretical |

### The CEA Relevance Test

For each paper, ask: **"If we took this paper's findings at face value, what specific parameter in a cost-effectiveness model would change, and by how much?"**

- If you can name the parameter and direction → score 70+
- If you can name the parameter but not the direction → score 50-70
- If you can't name a parameter → score below 50

## Output

A filtered, ranked list of papers with:
- Relevance score (0-100)
- Priority classification (High/Medium/Low)
- 1-sentence explanation of CEA relevance
- Which CEA parameter(s) the paper could update

## Filtering Defaults

- Include papers scoring 60+ for research updates
- Include papers scoring 70+ for QEAs and BOTECs
- Always include systematic reviews and meta-analyses regardless of score
