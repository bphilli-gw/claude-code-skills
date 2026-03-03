# Stage 0: Publication Readiness Assessment

You are a GiveWell editor assessing a Conditional Approval (CA) document for publication readiness. Your task is to thoroughly analyze the CA and determine how much work is needed to transform it into a publishable grant page.

## Your Task

Read the CA document provided at: $ARGUMENTS (or ask the user to specify the path to the CA document in the input/ folder)

Then produce a comprehensive **Publication Readiness Assessment** with the following components:

## 1. Section-by-Section Readiness Table

Create a table with these columns:
| CA Section | Quality (High/Med/Low) | Public-appropriate? | Sensitivity Issues | Footnote Gaps | Disposition |

**Disposition codes:**
- `USE`: Can publish as-is with footnote conversion
- `EDIT`: Good content, needs clarity/sensitivity edits
- `SUPPLEMENT`: Exists but needs expansion/context
- `DRAFT`: Missing or unsuitable; requires new writing
- `OMIT`: Internal-only content

## 2. Template Coverage Analysis

Compare the CA against the required grant page sections (from the template):
- In a nutshell
- 1. Summary (Background, What grant will do, Why we made it, Main reservations)
- 2. The organization
- 3. The intervention (including "Does it work?")
- 4. The grant (including budget)
- 5. The case for the grant (including cost-effectiveness)
- 6. Risks and reservations
- 7. Plans for follow up
- 8. Internal forecasts
- 9. Our process
- 10. Relationship disclosures

For each section, note whether the CA provides adequate content or if gaps exist.

## 3. Footnote Conversion Plan

List all CA references (internal models, emails, conversation notes, etc.) and map each to:
- (a) Equivalent public source that can be cited
- (b) Needs rewording to remove citation need
- (c) `BLOCKER` - material claim with no public source available

## 4. Sensitivity Scan

Identify any content that must be removed or anonymized:
- Internal emails or communications
- Evaluations of specific individuals
- Negotiation details
- Unpublished model parameters
- Non-public partner information

## 5. Key Strengths to Preserve

Identify passages in the CA that are particularly well-written and should be preserved with minimal editing. Quote these passages and note their location.

## 6. Overall Verdict

Provide one of:
- `Mostly ready` - Minor edits and footnote conversion needed
- `Moderate editing needed` - Some sections need rewriting, most content usable
- `Substantial rewriting needed` - Significant gaps or quality issues

Include a brief explanation of the main work required.

---

## Output Location

Save your assessment to: `output/[grant-name]/0-readiness-assessment.md`

Create the grant-name folder based on the grantee organization name (e.g., `output/malaria-consortium-chad-2025/`)

---

## Reference Documents

You have access to these reference documents in the context/ folder:
- Grant page template: `[TEMPLATE] Grant Page for [grant].md`
- Legibility guidance: `Legibility guidance_ grants pages, IRs, and simple CEAs (November 2023).md`
- Style guide: `GiveWell Style Guide (Claude).md`
- Example grant pages in `context/example-grant-pages/`

Consult these to understand quality standards and requirements.
