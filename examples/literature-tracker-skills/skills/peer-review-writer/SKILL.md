# Peer Review Writer

Produce a structured GiveWell-style peer review of a research document.

## When This Skill Applies

You need to review an intervention report, QEA, research memo, or other GiveWell research product. This skill produces the review itself — the `review-critic` skill then evaluates the review's quality.

## Inputs

- **Document to review**: Path to a `.md` or `.txt` file
- **Context** (optional): Supplementary documents for background
- **Related documents** (optional): Other documents for cross-referencing
- **CEA spreadsheet** (optional): CSV or XLSX file for cost-effectiveness analysis review
- **Skip literature research** (optional): If context is already provided

## Output

A markdown review saved to: `output/reviews/peer_review_[docname]_[date].md`

---

## Review Process

### Step 1: Read the Document

Read the full document. Before writing any feedback, form your own view:
- What question is the document trying to answer?
- What is its bottom-line conclusion?
- Do I buy it? Why or why not?
- What are the 2-3 assumptions that, if wrong, would most change the conclusion?
- Does the document already flag these? If so, do I agree with its best guesses?

### Step 1.5: Reviewer Intake (Interactive — Claude Code path only)

When running interactively via `/peer-review`, ask the user these questions before writing:

1. "What decision does this review inform?" (funding, deprioritization, deeper investigation, etc.)
2. "What are the 2-3 questions you'd most like my perspective on?"
3. "Is there a CEA spreadsheet I should review alongside the document? If so, provide a path."
4. "Are there parameters or assumptions you're least confident in?"
5. "Has anyone else reviewed this? What did they flag?"

If the user says "just review it cold" or doesn't answer, skip to Step 2.

Store the user's answers and reference them throughout the review (e.g., "You asked about the IV adjustment — here's my take").

### Step 2: Literature Research (unless skipped)

This is NOT just a spot-check. Do real research:

1. **Verify key citations** (2-3): Search for the most important cited studies using the `literature-search` skill. Note title, author, year, citation count, and DOI where available.
   - Do they exist? Are they real papers?
   - Does the document accurately represent their findings?

2. **Search for missing evidence** (5 queries): Think about what a skeptical reviewer would search for. Include:
   - Direct criticisms of the intervention or key studies
   - Alternative evidence on critical parameters (e.g., different effect sizes from other contexts)
   - Evidence from comparable interventions for cross-comparison (especially cash transfers)
   - Recent meta-analyses or systematic reviews the document may have missed
   - Implementation evidence (scale-up challenges, delivery costs, context dependence)

3. **For every claim you make in the review**, cite a specific source:
   - The document under review: [Document Section X.Y] or [Document p.N]
   - A paper found via search: (Author Year, "Title fragment", N citations)
   - Your own calculation: show the math

**Important caveat**: Semantic Scholar doesn't index everything. A paper not found in Semantic Scholar may still exist. Flag search failures as "could not verify" rather than "does not exist."

### Step 3: Write the Review

Use this exact five-section structure:

```markdown
# Peer Review: [Document Title]

**Reviewer**: AI Peer Reviewer (Claude)
**Date**: [date]
**Document reviewed**: [filename]

---

## 1. Reviewer Summary

### My understanding of this document
[2-3 sentences: what the document is about, what question it answers]

### In my words — the program and the case for it
[~100-150 words restating what the program does, the intuitive cost-effectiveness case
(key numbers), and the main uncertainties. This proves you understand the document
and surfaces any misunderstandings early.]

### My bottom line
[Take a stand. Do you buy the conclusion? What's your confidence level?
What would change your mind?]

### Key context
[Research stage (scoping/investigation/near-CA) and how it shapes your focus]

## 2. Cruxes and Decision-Relevant Feedback

[3-5 items. These are the things that would MOST CHANGE the funding decision
or research direction. Each item follows this format:]

### [Crux Title]

**The document's position:** [What the document says about this, with specific
section/page reference or direct quote]

**My position:** [Do you agree? If not, why? Where would you set the parameter
differently? Be specific — give numbers.]

**What I investigated:** [What you actually checked — calculations you reconstructed,
literature you searched, sense checks you ran. Show your work. Cite specific papers
by author, year, and title. If you tried and couldn't find anything, say so honestly.]

**How this could change the conclusion:** [Quantify if possible: "If X is wrong,
the CE ratio changes from Y to Z" or "This could shift the ranking relative to
cash transfers by N%"]

**What I'd recommend:** [Specific action — not "look into this" but "run this
specific analysis" or "talk to [type of expert]" or "here's why you should proceed
despite the uncertainty"]

## 3. Lower-Priority Feedback

[3-5 items. Important but unlikely to change the bottom line substantially.
Same format but briefer:]

### [Issue Title]

[Description + specific suggestion]

## 4. Sense Checks

### Comparisons to peer interventions
[How does this intervention compare to similar GiveWell programs? Include specific
numbers. How does it compare to cash transfers?]

### Literature research results
[What did the citation verification and gap search find? Report specific papers
with author, year, title, and what they show. If you found papers the document
missed, explain what they add.]

### What would a skeptic ask?
[2-3 key questions and whether the document answers them]

### Practical questions
[Implementation, delivery, scalability questions. Think like an implementer:
incentives, system constraints, interactions with existing programs, context match.]

## 5. Decision Questions

[Answer these directly — not "it would be worth considering" but your actual take:]

- **Should we fund more research or decide now?** [Given the current evidence,
  is additional investigation worth the cost and delay? Or is the picture clear
  enough to act on?]
- **If more research, what specifically?** [What would we study? How would we
  measure it? How generalizable would those results be? How additive would this
  be compared to existing literature on similar programs?]
- **How does this compare to the opportunity cost?** [Is the research team's time
  better spent here or elsewhere? How does this intervention compare to cash
  transfers and other GiveWell benchmarks?]
- **What's the simplest path to a decision?** [Is there a simpler version of this
  analysis that gets us to the same conclusion? Who should we talk to?]
```

---

## Anti-Restatement Rules

These are CRITICAL. The #1 failure mode of AI peer reviews is restating uncertainties the document already identifies.

**NEVER do this:**
- "The document acknowledges uncertainty about X. I agree this is uncertain and would want to see more evidence." (This wastes everyone's time — the author already knows.)
- "The adjustment factor is a key assumption." (Of course it is — the author said so. Tell me if it's WRONG.)
- "I'd want to see more evidence on Y." (Try to find that evidence yourself first. If you can't, explain what you tried.)
- "This is an important area for further research." (Be specific: what research? How would you measure it? Would you actually learn anything useful?)

**ALWAYS do this:**
- "The document assumes X=0.3. I'd set this at 0.45 instead, because [evidence/reasoning]. This changes the CE ratio from 8x to 5.5x." (Take a position with numbers.)
- "The document flags uncertainty about X but doesn't mention [related concern Z], which could matter because [reason]." (Surface NEW uncertainties.)
- "Given these uncertainties, I think we should [fund/investigate/deprioritize] because [reason]." (Answer the decision question.)
- "I searched for criticisms of [key study] and found [Author 2023] arguing [specific point]. The document should engage with this." (Do the research.)

---

## Calibration

Before writing, read these reference files for calibration on tone and depth:

- **Review guidance**: `reference/review-guidance/Things to look for when you're reviewing a GiveWell research product (1).md`
- **Legibility standards**: `reference/review-guidance/Legibility guidance for Claude (Feb 26) (1).md`
- **Example review (short, sharp)**: `reference/review-guidance/JM Review Notes - CHAI RDT_ACT in private sector (1).md`
- **Example review (thorough)**: `reference/review-guidance/Fortify Health open market grant renewal investigation (1).md`

### Key Calibration Points

From the examples, a good GiveWell review:
- **Takes a stand** — says "I buy this" or "I don't buy this" with reasons and numbers
- **Shows its work** — distinguishes "I checked and found X" from "I tried to check X but couldn't"
- **Prioritizes ruthlessly** — 4 sharp cruxes > 12 scattered observations
- **Quotes the document** — references specific passages, not vague impressions
- **Cites external evidence** — names specific papers, not "the literature suggests"
- **Asks decision questions** — "should we fund more research?" not just "this is uncertain"
- **Asks practical questions** — process, implementation, and scalability, not just methodology
- **Engages with the numbers** — reconstructs calculations, checks internal consistency, compares to benchmarks

## Cross-Referencing (when related documents provided)

When multiple related documents are provided:
- Note shared assumptions across documents
- Flag inconsistencies (different numbers for the same parameter)
- Identify where one document's weakness is another's strength
- Compare interventions head-to-head: which has better evidence? Better CE? More scalable?
- Suggest cross-pollination of evidence

## CEA Spreadsheet Review (when provided)

When a CEA spreadsheet (CSV or XLSX) is provided alongside the document:

1. **Read the spreadsheet** carefully (use Read tool for CSV, or the spreadsheet summary for XLSX)
2. **Cross-reference key parameters** between the document and spreadsheet:
   - Do the numbers in the document match the spreadsheet?
   - Are assumptions clearly labeled? Are any marked "complete guess" or uncertain?
3. **Check sensitivity**: Which parameters most affect the bottom line? Are the sensitive parameters well-evidenced or guesses?
4. **Spot-check arithmetic**: Pick 2-3 calculations and verify internal consistency (e.g., cost/beneficiary × beneficiaries = total cost)
5. **Include spreadsheet-specific findings** in your Cruxes section, with cell/tab references where possible (e.g., "CEA tab D24 assumes X, but...")

## Python Module (Optional)

For programmatic review with automated literature spot-check:
```bash
python -m review.peer_reviewer document.md
python -m review.peer_reviewer document.md --context supplementary.md
python -m review.peer_reviewer document.md --cea spreadsheet.csv
python -m review.peer_reviewer document.md --skip-lit-check
```
