# Literature Search

Search academic databases for papers relevant to a research question, intervention, or topic.

## When This Skill Applies

You need to find academic papers — for a QEA, research update, BOTEC evidence gathering, or any workflow that requires literature discovery.

## Inputs

- **Topic/query**: An intervention name, research question, or set of keywords
- **Date range** (optional): How far back to search (default: 2018-present)
- **Max results** (optional): How many papers to return (default: 50)

## Method

### Primary: Semantic Scholar API

Use the project's Python module for structured search:

```bash
python -c "
from literature.semantic_scholar import SemanticScholarAPI
api = SemanticScholarAPI()
results = api.search_papers('YOUR QUERY HERE', limit=50, year_range='2018-2025')
import json
print(json.dumps([{
    'title': p.get('title'),
    'authors': [a.get('name') for a in (p.get('authors') or [])[:3]],
    'year': p.get('year'),
    'abstract': (p.get('abstract') or '')[:300],
    'citationCount': p.get('citationCount'),
    'paperId': p.get('paperId'),
    'doi': (p.get('externalIds') or {}).get('DOI'),
    'openAccessPdf': (p.get('openAccessPdf') or {}).get('url'),
} for p in results], indent=2))
"
```

### Secondary: PubMed (for biomedical topics)

```bash
python -c "
from literature.pubmed_search import PubMedSearch
search = PubMedSearch()
results = search.search('YOUR QUERY HERE', max_results=20)
import json
print(json.dumps(results, indent=2))
"
```

### Tertiary: WebSearch (for grey literature, reports, WHO documents)

Use the WebSearch tool for non-indexed sources: WHO guidelines, GBD data, UNICEF reports, working papers.

## Search Strategy

1. **Start broad, then narrow.** Begin with the intervention name + "effectiveness" or "cost-effectiveness". Then add specific terms (population, geography, study type).

2. **Use multiple query variations.** Interventions have many names. For example, for seasonal malaria chemoprevention: "SMC", "seasonal malaria chemoprevention", "intermittent preventive treatment children", "SPAQ malaria".

3. **Check citation trails.** If you find a key paper, note its references and who cited it. High-citation papers in the field often lead to the most relevant evidence.

4. **Prioritize by study type:**
   - Systematic reviews / meta-analyses (highest value)
   - RCTs with pre-registered outcomes
   - Large observational studies with proper controls
   - Cost-effectiveness analyses
   - Modeling studies

## Output

Return a structured list of papers with:
- Title, authors, year
- Abstract summary (1-2 sentences)
- Study type (RCT, meta-analysis, observational, etc.)
- Why it's relevant to the research question
- DOI or Semantic Scholar link
- Open access PDF URL if available

Sort by relevance to the research question, not by citation count.

## What NOT to Do

- Do not summarize papers you haven't at least read the abstract of
- Do not fabricate paper titles or authors
- Do not claim a paper says something based on title alone
- If Semantic Scholar returns no results for a query, say so — do not make up results
