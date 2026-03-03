# Write-Review-Revise Loop Protocol

This skill defines the shared protocol for iterative quality improvement used by all workflows. When another skill or command asks you to "follow the review loop protocol," follow these instructions exactly.

## When This Skill Applies

A workflow command has told you to enter a write-review-revise loop. You will be told:
- Which **writer skill** to use (e.g., `botec-writer`, `qea-writer`)
- Which **reviewer skill** to use (e.g., `botec-reviewer`, `qea-reviewer`)

---

## The Protocol

### Step 1: WRITE

Produce the initial draft following the writer skill's instructions. Save it to the designated output path. Add a revision log at the top of the file:

```html
<!-- REVISION LOG
Document: [filename]
Writer: [skill name]
Reviewer: [skill name]
Created: [date]

Iteration 1:
  Status: DRAFT
  Blocking Issues: [pending]
-->
```

### Step 2: REVIEW

Switch to reviewer mode. **Read the ENTIRE output file from disk** using the Read tool — do not rely on your memory of what you just wrote. This is critical for honest self-evaluation.

Apply the reviewer skill's checklist and mandatory verification steps. Produce a structured verdict:

```markdown
## REVIEW VERDICT

**Document:** [filename]
**Iteration:** [N]
**Verdict:** APPROVED | REVISE

### CHECKLIST RESULTS

| # | Criterion | Pass/Fail | Evidence |
|---|-----------|-----------|----------|
| 1 | [from reviewer checklist] | PASS/FAIL | [specific quote or location] |

### BLOCKING ISSUES (must fix before APPROVED)

[Max 5 items. Only present if verdict is REVISE.]

1. **[Issue title]**
   - Location: [section or line reference in the document]
   - Problem: [specific, falsifiable statement of what's wrong]
   - Required fix: [concrete action — "add X" or "change Y to Z", not "consider X"]
   - Verification: [how to confirm the fix was applied correctly]

### NON-BLOCKING ISSUES

[Items noted but not worth another revision cycle]
```

### Step 3: DECIDE

- **APPROVED**: Update the revision log. Proceed to the next workflow stage.
- **REVISE**: Continue to Step 4.
- **Iteration 3 reached**: Stop the loop. Update the revision log with `MAX_ITERATIONS_REACHED`. Ask the user:
  > "I've completed 3 revision cycles. Remaining issues: [list]. Should I continue revising, or would you like to review the current version?"

### Step 4: REVISE

Read the reviewer's blocking issues. For each issue:
1. Determine the specific edit needed
2. Make the change in the output file using the Edit tool
3. Note the fix in the revision log

**Do NOT rewrite from scratch.** Edit the existing file to address specific issues. This preserves verified content (sourced numbers, calculation chains) and makes changes auditable.

Return to Step 2.

---

## Anti-Rubber-Stamp Rules

### First-Iteration Gate
On iteration 1, you **MUST** identify at least 2 blocking issues. The first draft is never perfect. If you cannot find 2 blocking issues, you are not looking hard enough — re-read the mandatory verification steps in the reviewer skill.

This rule does NOT apply to iterations 2+. By then the document may genuinely be ready.

### Adversarial Framing
When reviewing, adopt this stance:

> You are NOT the author. You are a skeptical GiveWell colleague who just received this document. Your reputation depends on catching real problems, not on being nice.

Before writing your verdict, ask yourself:
1. "Am I approving this because it's actually good, or because I wrote it and don't want to redo work?"
2. "If a number in this document is wrong by 50%, does anyone get hurt?"
3. "What would an experienced GiveWell researcher flag that I'm missing?"

### Re-Read From Disk
Always re-read the file using the Read tool before reviewing. Never review from conversational memory. This creates a separation between "writer mode" and "reviewer mode."

### Blocking Issue Cap
Maximum 5 blocking issues per review. This prevents infinite nitpicking and forces you to prioritize what actually matters most.

---

## User Checkpoints

After the loop completes (APPROVED or MAX_ITERATIONS_REACHED), present to the user:
- The final document's bottom line / key conclusion
- Number of revision iterations completed
- Any remaining non-blocking issues
- Ask: "Would you like to review this before I proceed?"

For high-stakes workflows (/qea, /botec), also checkpoint **after iteration 1** to show the user the initial estimate and key issues before further revision.
