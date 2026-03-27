# GiveWell-Style Footnotes

Convert a research document's factual claims into verified footnotes with direct source quotes.

## When This Skill Applies

You have a markdown document (QEA, research update, memo) that contains factual claims — some with inline citations, some without — and you want every claim backed by a footnote containing a hyperlinked source and a direct quote from that source.

## Inputs

- **File path**: Path to the markdown document to annotate
- **Scope** (optional): "full" (default) processes the entire document; "section" processes only a named section; "summary-only" processes only the summary

## What a GiveWell-Style Footnote Looks Like

Each footnote has three parts:

```markdown
[^N]: [Author Year](URL): "Exact quote from the source supporting the claim." Any verification notes.
```

1. **Hyperlinked source** — author, year, and a working URL (DOI, PMC, or direct link)
2. **Direct quote** — the actual sentence or passage from the source that contains the data point or finding. Not a paraphrase.
3. **Verification notes** — corrections, caveats, or flags for manual follow-up

Example:

```markdown
Neonatal mortality in SSA is ~27/1,000 live births.[^4]

[^4]: [WHO Newborn Mortality Fact Sheet](https://www.who.int/news-room/fact-sheets/detail/newborn-mortality): "Sub-Saharan Africa had a neonatal mortality rate of 27 deaths per 1,000 live births in 2022, the highest in the world." Source: UN IGME 2024.
```

## Method

### Step 1: Extract claims

Scan the document and build a numbered list of every factual claim that needs a source. A "factual claim" is any statement that asserts a specific number, finding, causal relationship, or characterization of evidence. For each claim, record:

- The claim text (the sentence or clause)
- The existing citation, if any (e.g., "Keats et al. 2019", a DOI, a URL)
- Whether the claim currently has a citation or is uncited
- The section of the document it appears in

**Include both cited and uncited claims.** Uncited claims are the highest priority — they are the most likely to be wrong or unsupported.

Present the full claim list to the user before proceeding.

### Step 2: Check for local full text

Before fetching anything from the internet, check the repository for PDFs or notes that may already contain the source text:

```bash
# Check for existing PDFs
find ./articles/ -name "*.pdf" 2>/dev/null
# Check for split PDF notes
find ./articles/ -name "notes.md" 2>/dev/null
# Check for any downloaded papers in the working directory
find . -name "*.pdf" -not -path "./.git/*" 2>/dev/null
```

If a relevant PDF exists locally:
- Use the `/split-pdf` skill to read it (do NOT read a full PDF directly)
- Extract the exact quote supporting the claim from the split notes
- This is far more reliable than abstract-only verification

### Step 3: Attempt to retrieve full text for sources not already local

For each source that is not already in the repo, attempt to download full text using the project's PDF retriever:

```python
from literature.pdf_retriever import PDFRetriever
retriever = PDFRetriever(unpaywall_email="your@email.com")
result = retriever.find_pdf(
    {"doi": "10.xxxx/xxxxx", "title": "Paper Title"},
    download=True,
    output_dir="./articles"
)
```

Chain sources in order:
1. Semantic Scholar open access PDF
2. Unpaywall (requires DOI)
3. PubMed Central (for biomedical papers with PMID)
4. CORE (institutional repositories)

If a PDF is downloaded, use `/split-pdf` to read it and extract quotes.

### Step 4: Fall back to abstracts and web sources

For sources where full text is unavailable:
1. Fetch the PubMed abstract via the PubMed API or web fetch of `https://pubmed.ncbi.nlm.nih.gov/PMID/`
2. Fetch NCBI Bookshelf pages for WHO guidelines (e.g., `https://www.ncbi.nlm.nih.gov/books/NBKXXXXXX/`)
3. Fetch WHO fact sheets, UNICEF data pages, or other institutional sources directly
4. Use WebSearch as a last resort to find the specific data point

**Critical: if you cannot find the exact quote, do not fabricate one.** Flag the claim for manual verification instead.

### Step 5: Verify each claim against the source

For each claim, compare the document's assertion against the source text:

| Outcome | Action |
|---------|--------|
| **Source confirms claim exactly** | Write footnote with direct quote |
| **Source confirms claim approximately** | Write footnote with quote; note the discrepancy (e.g., "paper says 19.3%, QEA rounds to ~19%") |
| **Source contradicts claim** | Write footnote with quote; **correct the claim in the document**; note the correction |
| **Source doesn't contain the specific data point** | Write footnote noting what the source does say; flag with "**Full text verification needed**" |
| **Source is inaccessible** | Write footnote with URL; flag with "**Manual verification needed**" |
| **Claim is uncited and no source found** | Flag with "**Needs citation**" — suggest a possible source if one seems likely |

### Step 6: Convert to footnotes

1. **Replace inline citations** with footnote markers: `(Keats et al. 2019)` → `[^N]`
2. **Add markers to uncited claims** that now have sources: `[^N]`
3. **Write footnote definitions** at the end of the document in the format: `[^N]: [Source](URL): "quote." Notes.`
4. **Deduplicate thoughtfully** — if the same source supports multiple claims, each footnote should contain the specific quote for that specific claim (the same paper may appear in multiple footnotes with different quotes)

### Step 7: Validation

Run a consistency check:

```python
import re
with open('path/to/file.md', 'r') as f:
    content = f.read()
refs = sorted(set(int(m) for m in re.findall(r'\[\^(\d+)\](?!:)', content)))
defs = sorted(set(int(m) for m in re.findall(r'^\[\^(\d+)\]:', content, re.MULTILINE)))
missing_defs = set(refs) - set(defs)
unused_defs = set(defs) - set(refs)
if missing_defs: print(f'References without definitions: {sorted(missing_defs)}')
if unused_defs: print(f'Definitions without references: {sorted(unused_defs)}')
if not missing_defs and not unused_defs: print('All footnotes matched!')
```

Report the results to the user.

## Parallelization

Use parallel agents to speed up source verification. Group claims by source — all claims citing the same paper can be verified by a single agent that fetches and reads that paper once. A typical document might need 5-10 agents, each handling 1-3 sources.

Each agent should:
1. Fetch or read the source (full text if available, abstract if not)
2. Find the exact quote supporting each assigned claim
3. Return: quote found (with text), claim unsupported (with what the source does say), or source inaccessible

## What NOT to Do

- **Do not fabricate quotes.** If you can't find the exact text, say so. A flagged footnote is infinitely better than a hallucinated one.
- **Do not paraphrase and present as a quote.** Quotes must be verbatim from the source. Use ellipsis (...) to skip irrelevant middle text.
- **Do not skip uncited claims.** These are the most important to check — they're the ones most likely to be wrong.
- **Do not rely on memory of what a paper says.** Always fetch the actual source text. Memory of paper contents is unreliable and a major source of hallucination.
- **Do not read full PDFs directly.** Always use the split-pdf workflow for papers longer than ~15 pages.
- **Do not silently correct claims.** If you find an error, note the correction in the footnote so reviewers can see what changed and why.

## Output

The skill modifies the input file in place:
- Inline citations replaced with footnote markers
- Uncited claims annotated with footnote markers
- Footnote definitions added at end of document
- Any factual corrections applied to body text (with footnote noting the correction)
- Verification summary printed to console:
  - N claims verified with direct quotes
  - N claims verified from abstracts only (full text would improve)
  - N claims flagged for manual verification
  - N factual corrections made
  - N uncited claims that still need sources
