# Peer Review

Run a peer review on an intervention report, research memo, or other GiveWell research product.

**Argument:** $ARGUMENTS (path to the document to review)

---

## Workflow

1. **Load the document** at the specified path. If no path is given, ask the user which document to review. Check `reference/intervention-reports/` for available IRs.

   **If the document is a Google Doc**, also read its comments (use `read_document_comments`). Author comments are important context — they flag sections the author knows are incomplete, questions they want help with, and shortcuts they've noted. Treat these as part of the document, not background noise.

2. **Load reference materials** from `reference/review-guidance/` for calibration:
   - Review guidance ("Things to look for when you're reviewing...")
   - Legibility guidance
   - Example reviews (CHAI, Fortify Health)

3. **Initial literature spot-check with PDF grounding**
   - Extract the intervention topic, key citations, and search terms from the document
   - Search Semantic Scholar for: cited study verification + related/missing literature
   - Download full-text PDFs for all found papers via `literature/pdf_retriever.py` (Semantic Scholar → Unpaywall → PMC → CORE chain)
   - Split downloaded PDFs and read key sections for extraction notes
   - Flag each paper as FULL TEXT AVAILABLE or FULL TEXT NOT AVAILABLE

4. **Run the peer review with iterative literature searches**

   Use the system prompt and output format from `review/peer_reviewer.py`. **As you draft each section**, search for additional supporting evidence:

   - **Before writing each crux**: Search for literature that supports or challenges the specific claim you're making. Don't rely on training knowledge alone — find the paper, get the PDF if possible, and cite it.
   - **When making any empirical claim** (e.g., "agriculture was less affected during COVID"): Stop and search for a specific source. If you can't find one, either drop the claim or explicitly flag it as unverified.
   - **For each literature search during writing**: Use WebSearch or Semantic Scholar to find papers, then attempt PDF retrieval for any new papers found. If full text is unavailable, do NOT cite the paper as if you've read it — flag grounding level.

   Output sections:
   1. **REVIEWER SUMMARY** — understanding, bottom line, skeptic flags
   2. **CRUXES AND DECISION-RELEVANT FEEDBACK** — 3-5 items that would most change the funding decision
   3. **SKEPTIC AND PRACTICAL QUESTIONS**
   4. **LOWER-PRIORITY FEEDBACK** — 3-5 items
   5. **LITERATURE AND EVIDENCE CHECKS** — papers found/verified, missing literature, discrepancies
   6. **DECISION QUESTIONS** — fund now, investigate more, or deprioritize?

   **Balance quantitative and qualitative considerations.** The CEA is only part of the story. GiveWell funding decisions also weigh implementation quality, context fit, learning value, strategic portfolio considerations, and qualitative judgment. Do not let CE ratios dominate your cruxes or decision recommendations — if the qualitative case is strong but CE is marginal (or vice versa), say so explicitly. A review that only engages with the numbers misses half the picture.

5. **Citation verification pass (MANDATORY)**

   Before saving the review, scan every empirical claim and verify:
   - Does it have a specific citation with a DOI or URL? If not, search for one now or remove the claim.
   - If citing a paper with specific findings (effect sizes, directions, mechanisms): is the claim grounded in actual PDF text you read? If you only read the abstract, downgrade the claim to "this paper exists and appears relevant" — do not cite specific findings you haven't verified in the full text.
   - If no source can be found: remove the claim entirely. Do NOT leave uncited empirical assertions in the final product.
   - Count how many of your cited papers have full-text grounding vs. abstract-only. If fewer than half of your crux-supporting citations have full-text grounding, stop and retrieve more PDFs before finalizing.

   This pass exists because previous reviews allowed vague, uncited claims like "the literature confirms X" to slip through. Every factual claim must have a traceable source.

6. **Anti-rehashing pass (MANDATORY)**

   Before saving, re-read the original document (and its comments/highlights) and check each piece of feedback:
   - **Does the document already flag this as a limitation or reservation?** If yes, do not restate it as a critique. Instead, engage with the author's treatment: do you agree with their framing? Would you set the parameter differently? Can you add evidence they didn't have? If you can't add anything beyond what the author already wrote, delete the feedback item.
   - **Is this flagged as known-incomplete in the doc?** Sections marked with comments like "still to be written," yellow highlighting, XXXX placeholders, or "rough" disclaimers should NOT be critiqued for being incomplete. The author knows. Skip these unless you have something constructive to offer about the content direction.
   - **Did the author ask a question in a comment?** If the author flagged uncertainty or asked for input via a doc comment, engage with it directly. These are invitations to help, not things to note as weaknesses. Try to answer the question, suggest an approach, or point to evidence that could resolve it.

   This pass exists because previous reviews wasted researcher time by restating the author's own reservations back to them and flagging known-incomplete sections as weaknesses.

7. **Save the review** to `output/reviews/peer_review_<document>_<date>.md`

---

## Citation Rules (CRITICAL)

These rules address feedback from peer reviewers who found citation errors in previous reviews:

- **Hyperlink all citations** using DOI: `[Author Year](https://doi.org/DOI)`. If no DOI, use the best available URL.
- **Never assert journal placement** (e.g., "published in AER") unless confirmed in paper metadata. Use author/year/title only.
- **Ground claims in paper text**: Only assert findings about a paper if confirmed in the downloaded PDF or extraction notes.
- **No full text = no specific findings.** If you cannot obtain the full text of a paper, you may note that it exists and appears relevant, but you MUST NOT cite specific effect sizes, directions of effect, subgroup results, or mechanisms from it. Saying "Verified against abstract" is not verification — abstracts lack the detail needed to accurately characterize findings, and relying on them produces mischaracterizations that look like hallucination to the researcher. The only claims you can make from an abstract are: the paper exists, its general topic, and its sample/setting.
- **No rehashing**: See the anti-rehashing pass (step 6) for the full rule. In short: do not restate concerns the document already addresses — engage with them or skip them.

---

## Optional Flags

The user may specify:
- **CEA spreadsheet**: A CSV or XLSX file to cross-reference with the document (e.g., `--cea "RTV simple BOTEC.xlsx"`)
- **Related documents**: Other documents being reviewed alongside this one for cross-referencing
- **Skip lit check**: Skip the literature spot-check for a faster review

---

## Example Usage

```
/peer-review reference/intervention-reports/bundled-inputs/Raising the Village IR.md
/peer-review reference/intervention-reports/Updated nets intervention report 2025 v2.md
```
