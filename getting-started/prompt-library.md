# AI Prompt Library for GiveWell Research

*Last updated: February 2026*   
*Author: Brendan*

Ready-to-use prompts organized by task type. Copy, paste, and adapt the parts in \[brackets\]. These are starting points — iterate from here.

**How to use this**: Find the task closest to what you're doing, copy the prompt, fill in the brackets, and paste it into Claude (or whichever tool you're using). You don't need to use every section of every prompt, trim what isn't relevant.

**Companion resources:**

- [AI Quick Start Guide](https://docs.google.com/document/d/1R589GtPZu-ACmyfWuQnviWSKhovcn2FyiZmv4rT3JP8/edit?tab=t.0#heading=h.8agw41ulf6qz) — Prompting tips, tool recommendations, and how to reduce hallucinations  
- [AI Success Stories](https://docs.google.com/document/d/1UreciwXpQPCcJnRO3Pws7YKM9hJ8f6ZNmpmzGue4Qxs/edit?tab=t.jz09888uk22i) — Examples from staff of workflows that worked well  
- [\#ai-discussion](#) — Slack channel for questions and tips

**Table of Contents**

[Research & Analysis](#research-&-analysis)

[Summarize a paper](#summarize-a-paper)

[Literature landscape for a new topic](#literature-landscape-for-a-new-topic)

[Quick evidence assessment](#quick-evidence-assessment)

[Interpret outcome measures or units](#interpret-outcome-measures-or-units)

[Extract key parameters from a study](#extract-key-parameters-from-a-study)

[Writing & Editing](#writing-&-editing)

[Edit for GiveWell legibility](#edit-for-givewell-legibility)

[Draft a check-in](#draft-a-check-in)

[Clean up rough notes or voice memos](#clean-up-rough-notes-or-voice-memos)

[Write a meeting summary](#write-a-meeting-summary)

[Document Analysis](#document-analysis)

[Digest a long internal document](#digest-a-long-internal-document)

[Find specific information across documents](#find-specific-information-across-documents)

[Email & Communication](#email-&-communication)

[Draft an email](#draft-an-email)

[Prepare for a grantee or external call](#prepare-for-a-grantee-or-external-call)

[Translate and adapt for Francophone partners](#translate-and-adapt-for-francophone-partners)

[Thought Partnership](#thought-partnership)

[Get pushback on your reasoning](#get-pushback-on-your-reasoning)

[Brainstorm approaches to a problem](#brainstorm-approaches-to-a-problem)

[Predict questions before a check-in or meeting](#predict-questions-before-a-check-in-or-meeting)

[Stress-test a grant recommendation](#stress-test-a-grant-recommendation)

[Spreadsheets & Data](#spreadsheets-&-data)

[Write or explain a spreadsheet formula](#write-or-explain-a-spreadsheet-formula)

[Extract data from a PDF table](#extract-data-from-a-pdf-table)

[Structured Tasks](#structured-tasks)

[Generate interview or focus group questions](#generate-interview-or-focus-group-questions)

[Synthesize multiple documents into a guidance doc](#synthesize-multiple-documents-into-a-guidance-doc)

## Research & Analysis {#research-&-analysis}

### Summarize a paper {#summarize-a-paper}

Good for getting a quick read on whether a paper is worth digging into. Can do multiple at once. 

```
I'm uploading [paper title/PDF]. Please summarize:

1. The main research question
2. Study design and methods (sample size, setting, duration)
3. Key findings (with effect sizes and confidence intervals if available)
4. Limitations the authors acknowledge
5. How this might be relevant to [your topic — e.g., "GiveWell's assessment of
   seasonal malaria chemoprevention" or "whether vitamin A supplementation
   reduces child mortality"]

Quote specific passages to support your summary. Flag if anything seems
inconsistent between the abstract and the results.
```

### Literature landscape for a new topic {#literature-landscape-for-a-new-topic}

Good for getting an initial overview when scoping a new intervention or investigation. Best with a tool that has web search enabled. You can also turn on Deep Research mode for more in-depth academic literature reviews. 

```
I'm doing an initial assessment of [intervention/topic — e.g., "post-discharge
malaria chemoprevention"].

Please help me map the evidence landscape:

1. What are the key RCTs or systematic reviews on this topic? List the most
   important 5-10 studies with authors, year, and one-sentence finding.
2. What is the overall direction of the evidence? (Strong, moderate, mixed,
   weak?)
3. What populations and settings have been studied?
4. What are the main evidence gaps — what hasn't been well studied?
5. Are there any ongoing or recently completed trials I should know about?

Focus on studies most relevant to low- and middle-income country settings.
I'll verify everything you find, so note where you're uncertain.
```

### Quick evidence assessment {#quick-evidence-assessment}

Use this when you need to form a quick take on a specific empirical claim — e.g., for a check-in or to decide whether something is worth deeper investigation.

```
I need to assess the evidence on [specific claim — e.g., "whether
insecticide resistance reduces the effectiveness of bednets" or "the mortality
impact of deworming"].

Here's what I already know or believe: [brief summary of your current view]

Please find:
1. What does the best available evidence say? Summarize the 3-5 most relevant
   studies or reviews.
2. How strong is this evidence? (Study quality, consistency, sample sizes)
3. What's your best read on whether this claim is likely true, and how
   confident should I be?
4. What are the biggest sources of uncertainty?
5. What would I look into next if I had more time?

Be specific with numbers where possible. Tell me when you're unsure.
```

### Interpret outcome measures or units {#interpret-outcome-measures-or-units}

Useful when you encounter unfamiliar metrics in papers — e.g., what does a biomarker level mean, or how to convert between units.

```
I'm reading a study on [topic] and I need help understanding [outcome measure
— e.g., "hemoglobin levels measured in g/dL" or "malaria parasite density per
microliter"].

Please explain:
1. What does this measure actually capture?
2. What are normal/healthy ranges vs. concerning ranges?
3. How does [specific value from the study] compare to those ranges?
4. Are there any important caveats about how this is measured (e.g., finger
   prick vs. venous blood)?
5. How does this relate to [the outcome I care about — e.g., "mortality risk"
   or "functional impairment"]?
```

### Extract key parameters from a study {#extract-key-parameters-from-a-study}

For pulling numbers you need for a cost-effectiveness model or BOTEC.

```
I'm uploading [paper/document]. I need to extract specific parameters for a
cost-effectiveness estimate.

Please find and report the following (with page/table references):

[List the specific parameters you need, e.g.:]
- Effect size (relative risk reduction or odds ratio) for [primary outcome]
- Baseline rate of [outcome] in the control group
- Cost per person treated (if reported)
- Duration of follow-up
- Coverage rate achieved
- Any reported adverse effects rate

For each parameter, note:
- The exact value and confidence interval
- Where in the paper it appears
- Any caveats (e.g., per-protocol vs. intention-to-treat)

If a parameter isn't reported in the paper, say so — don't estimate.
```

## Writing & Editing {#writing-&-editing}

### Edit for GiveWell legibility {#edit-for-givewell-legibility}

Use this to improve your writing to match GiveWell's style: clear bottom lines, plain language, honest uncertainty, and specific claims. Based on our legibility guidance.

```
Please edit the following text to be more legible in GiveWell's style. That
means:

- Lead with a clear bottom line — what do I think, and how confident am I?
- Use plain language (not academic or consultant-speak)
- Be specific — use numbers instead of vague words like "many" or "significant"
- Be honest about uncertainty — say what I don't know and why it matters
- Structure as: what I think → why I think it → how I could be wrong

Keep my meaning and conclusions intact, but make it easier for a busy reader
to quickly grasp the key points and disagree if they want to.

Flag anything that seems unclear or where you think I'm being vague about what
I actually believe.

[Paste your text here]
```

See also a legibility project set up by Katie [here](https://claude.ai/project/019c0c02-0f9c-725b-9868-47fa06232618) that you can just paste your text into. 

### Draft a check-in {#draft-a-check-in}

For writing a structured check-in to your manager on an investigation or project.

```
Help me draft a check-in on [project/investigation — e.g., "my investigation
into post-discharge malaria chemoprevention"].

Here's where I am:
- What I've done: [brief summary of work so far]
- What I'm finding: [key findings or observations]
- What I think: [your current bottom line, even if tentative]
- What I'm unsure about: [main uncertainties]

Please structure this as a concise check-in (half page max) with:
1. Bottom line — if I stopped now, what would I recommend?
2. Why I think that — key reasons (2-3 sentences)
3. Key uncertainties — what could change my mind (ranked by importance)
4. Next steps — what I'll look into next and roughly how long it'll take

Keep it in plain language. My manager [knows the background well / needs some
context on what this project is].
```

### Clean up rough notes or voice memos {#clean-up-rough-notes-or-voice-memos}

For turning messy notes into something structured and readable.

```
Here are my rough notes from [context — e.g., "a call with a grantee" or
"reading through an intervention report" or "thinking through a problem"].

Please clean these up into organized notes. Preserve all the substance — don't
add information or interpretation I didn't include. Just:
- Fix grammar and incomplete sentences
- Group related points together
- Add brief headers for each topic
- Flag anything that seems incomplete or unclear with [?]

[Paste your notes here]
```

### Write a meeting summary {#write-a-meeting-summary}

```
Here are my notes from [meeting type — e.g., "a call with Malaria Consortium"
or "our pod meeting on nutrition grants"].

Please write a brief summary with:
1. Key decisions made (if any)
2. Main discussion points (3-5 bullets)
3. Action items (who is doing what, by when)
4. Open questions that weren't resolved

Keep it to one page. Use the participants' names where relevant.

[Paste your notes or transcript here]
```

See also Andrew M’s project for having AI write GiveWell-style conversation notes [here](https://www.givewell.org/research/conversations). 

## Document Analysis {#document-analysis}

### Digest a long internal document {#digest-a-long-internal-document}

For quickly getting up to speed on a long IR, CA, or other internal document. Works best when you upload or link to the actual document.

```
I need to get up to speed on [document — e.g., "this intervention report on
seasonal malaria chemoprevention" or "this conditional approval for AMF"].

Please give me:
1. The bottom line — what does this document conclude or recommend?
2. The key evidence and reasoning behind that conclusion (5-7 bullets)
3. The main uncertainties or risks flagged
4. Any specific numbers I should know (cost per life saved, effect sizes, etc.)
5. What open questions remain

I have [amount of time — e.g., "15 minutes" or "an hour"] before [context —
e.g., "a meeting about this grant" or "I need to start my review"]. Focus on
what's most important for that.
```

### Find specific information across documents {#find-specific-information-across-documents}

When you need to search through multiple documents for specific details.

```
I'm uploading [number] documents related to [topic — e.g., "our conditional
approvals for vitamin A supplementation grants"].

I need to find [what you're looking for — e.g., "what coverage targets each
grantee committed to" or "what monitoring requirements we set" or "any
mentions of supply chain concerns"].

For each document, report:
- Document name
- Relevant passage (quoted)
- Your one-sentence summary of what it says

If a document doesn't contain what I'm looking for, just note that.
Organize the results in a table if possible.
```

## Email & Communication {#email-&-communication}

### Draft an email {#draft-an-email}

```
Help me draft an email to [recipient and their role — e.g., "a program officer
at Malaria Consortium" or "a colleague asking about our investigation"].

Context: [Brief background on the situation]
Goal: [What you want to achieve — e.g., "request updated data by next month"
or "give them a status update on our review"]
Tone: [Professional/casual/warm — default to professional but friendly]
Length: [Brief/moderate — most emails should be short]

Key points to include:
- [Point 1]
- [Point 2]
- [Point 3]

[Optional: "Check my Gmail for our most recent exchange to match the tone and
pick up where we left off."]
```

### Prepare for a grantee or external call {#prepare-for-a-grantee-or-external-call}

```
I have a call with [person/org — e.g., "the Malaria Consortium team about
their DRC bednet distribution"] on [date/time].

The purpose of the call is: [goal — e.g., "to discuss their updated budget
and timeline for Phase 2"]

Here's the background: [brief context, or upload relevant documents]

Please help me prepare:
1. Key questions I should ask (prioritized — what's most important?)
2. Key facts I should have at hand from the attached documents
3. Potential difficult topics or pushback I should be ready for
4. A brief agenda I could share in advance (if appropriate)
```

### Translate and adapt for Francophone partners {#translate-and-adapt-for-francophone-partners}

```
Please translate the following into French. This is for [context — e.g.,
"an email to a grantee in DRC" or "survey questions for beneficiaries
in Burkina Faso"].

Use [formal/informal] French. Keep the meaning precise — don't paraphrase
in ways that could change the substance.

If any terms are ambiguous or have different translations depending on
context, flag them and suggest options.

[Paste your text here]
```

## Thought Partnership {#thought-partnership}

### Get pushback on your reasoning {#get-pushback-on-your-reasoning}

```
I'm thinking through [topic/decision]. Here's my current reasoning:

[Your reasoning — be specific about what you believe and why]

Please think about:
1. What are the weakest points in this reasoning?
2. What considerations am I missing or underweighting?
3. Play devil's advocate — make the best case against my conclusion
4. If you were reviewing this as a GiveWell colleague, what questions would
   you ask?

Push back hard. I'd rather hear tough critiques now than miss something
important.
```

### Brainstorm approaches to a problem {#brainstorm-approaches-to-a-problem}

```
I need to [task/goal — e.g., "figure out how to estimate the impact of this
nutrition program without good baseline data" or "decide how to prioritize
five potential grants with limited investigation time"].

Context: [Relevant background]
Constraints: [Time, resources, requirements]

Before brainstorming, search the web for how other organizations or
researchers have approached [this type of problem]. Then generate 5-7
different approaches with brief pros/cons for each.

Rank them by which you think is most promising given my constraints.
```

### Predict questions before a check-in or meeting {#predict-questions-before-a-check-in-or-meeting}

For anticipating what your manager or colleagues will ask about your work.

```
I'm about to [check in with my manager / present to the team / meet with
pod leads] about [topic].

Here's what I'm planning to share:
[Your main points or draft]

Based on this, what questions are they most likely to ask? Think about:
- Gaps in my reasoning or evidence
- Alternative interpretations I haven't addressed
- Practical concerns about implementation or next steps
- Things that seem too vague or uncertain

Give me the top 5-7 likely questions and suggest a brief answer or
talking point for each.
```

### Stress-test a grant recommendation {#stress-test-a-grant-recommendation}

```
I'm [recommending / leaning toward recommending] a grant of [$amount] to
[organization] for [program].

Here's my case:
[Brief summary of why you think this is a good grant]

Key assumptions:
[List your main assumptions — e.g., "coverage will reach 80%", "the effect
size from the Kenya trial generalizes to DRC"]

Please stress-test this:
1. Which assumptions are most fragile? What happens if they're wrong?
2. What are the strongest arguments against this grant?
3. What would a skeptical GiveWell researcher push back on?
4. Are there important risks I haven't mentioned?
5. What evidence would change your assessment?

Be specific — don't just say "implementation might be challenging." Tell me
what specific implementation risk you're worried about and why.
```

## Spreadsheets & Data {#spreadsheets-&-data}

### Write or explain a spreadsheet formula {#write-or-explain-a-spreadsheet-formula}

For ChatGPT (since it can work with Excel files) or for pasting formulas into any chat tool.

```
[To write a formula:]
I need a Google Sheets formula that [what you want — e.g., "looks up a
country name in column A of Sheet2 and returns the corresponding mortality
rate from column D, defaulting to 0 if not found"].

The data is structured like: [describe your layout or paste a few rows]

[To explain a formula:]
Can you explain what this formula does step by step? I inherited this
spreadsheet and I'm not sure what this is calculating.

[Paste the formula]

Tell me:
1. What it does in plain English
2. What each part of the formula contributes
3. Any edge cases where it might give unexpected results
```

### Extract data from a PDF table {#extract-data-from-a-pdf-table}

Works best with Claude Code or ChatGPT. For complex extractions, consider asking Brendan about using Claude Code.

```
I'm uploading a PDF that contains [describe what — e.g., "DHS survey results
for malaria prevalence by region" or "a budget table from a grantee report"].

Please extract [specific data — e.g., "the malaria prevalence rates by
region from Table 3"] and format it as a CSV table with columns:
[List your desired columns]

Double-check your extraction against the source. Flag any values that are
hard to read or that you're uncertain about.
```

## Structured Tasks {#structured-tasks}

### Generate interview or focus group questions {#generate-interview-or-focus-group-questions}

```
I'm [preparing for interviews / designing focus group questions] about
[topic — e.g., "how community health workers spend their time during
bednet distributions" or "beneficiary experiences with the nutrition
program"].

The goal is to understand: [what you want to learn]
Participants will be: [who — e.g., "CHWs in rural DRC" or "mothers of
children under 5"]

Please generate 10-15 questions that:
- Start broad and get more specific
- Use open-ended language (not yes/no)
- Avoid leading or loaded phrasing
- Are practical to ask in [setting — e.g., "a 45-minute group discussion"
  or "a short household survey"]

Group them by theme. Flag any questions that might be sensitive or need
careful framing.
```

### Synthesize multiple documents into a guidance doc {#synthesize-multiple-documents-into-a-guidance-doc}

For combining information from several sources into a coherent reference document.

```
I'm uploading [number] documents about [topic — e.g., "our approach to
adjusting for external validity across different grantmaking areas"].

Please synthesize these into a single guidance document that:
1. Starts with a clear summary of the overall approach
2. Organizes the key points by theme (not by source document)
3. Notes where the documents agree and where they differ
4. Highlights any gaps — things none of the documents address well
5. Includes specific examples and numbers from the source documents

Target length: [e.g., "3-5 pages"]. Write it so someone unfamiliar with
these individual documents could understand our approach.
```
