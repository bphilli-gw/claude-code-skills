# Things to Try with AI at GiveWell

*Last updated: February 2026*
*Author: Brendan*

A list of concrete things you can try with AI, roughly ordered from simple to complex. Each one should take 5-30 minutes. You don't need to do these in order or do all of them — pick what's relevant to your work right now and skip what isn't.

**Before you start**: Make sure you've read the [AI Quick Start Guide](https://docs.google.com/document/d/1R589GtPZu-ACmyfWuQnviWSKhovcn2FyiZmv4rT3JP8/edit?tab=t.0#heading=h.8agw41ulf6qz) and have access to Claude. If you need help with anything on this list, reach out to Brendan or ask in #ai-discussion.

See the [Prompt Library](prompt-library.md) for ready-to-use prompts for many of these tasks.

---

## Getting started

These are the basics. If you haven't done these, start here.

**1. Just have a conversation.** Open Claude and tell it what you're working on today. Ask it a question about your work — anything. The goal is just to get comfortable talking to it. There's no wrong way to start.

**2. Ask AI to edit something you've written.** Take a paragraph from a draft email, check-in, or write-up and paste it in. Ask: *"Edit this for clarity and concision. Preserve my meaning but make it easier to read."* Compare the result to your original.

**3. Upload a document and ask a question about it.** Take a paper, IR, or CA you're reading and upload it (or point Claude to it in Drive). Ask something specific: *"What are the key uncertainties mentioned in this document?"* or *"Summarize the cost-effectiveness section."*

**4. Turn on Claude's connectors.** Go to Settings → Connectors and enable Google Drive, Gmail, Slack, and Asana. Then enable Memory under Settings → Capabilities. These make Claude much more useful over time. (See the Quick Start Guide for details.)

**5. Ask AI to explain something.** Next time you encounter something unfamiliar — a statistical method, a formula someone else wrote, a policy term — just ask. *"Explain what a difference-in-differences design is and when researchers use it"* or paste a formula and ask *"What does this do?"*

## Day-to-day workflow

Things that can slot into your regular work right away.

**6. Summarize a paper before you read it.** Upload a PDF and ask for a summary of the research question, methods, key findings, and limitations. Use this to decide whether the paper is worth a deeper read. (See the Prompt Library for the full prompt.)

**7. Prepare for a meeting or call.** Before your next grantee call or check-in, tell Claude what the meeting is about, upload any relevant docs, and ask it to help you prepare key questions and an agenda. Works especially well for calls where you need to quickly get up to speed on background.

**8. Draft an email you've been putting off.** Give Claude the recipient, context, goal, and key points. Review and rewrite in your own voice. This is especially useful for emails where you're struggling with tone or structure — the first draft breaks the blank page problem.

**9. Clean up your notes.** After a call or meeting, paste your rough notes and ask Claude to organize them with headers, fix incomplete sentences, and flag anything unclear. This is one of the highest-value, lowest-risk uses — you wrote the content, AI just makes it readable.

**10. Get help with a spreadsheet formula.** Next time you need to write a VLOOKUP, SUMIFS, or anything more complex, describe what you want in plain English and let AI write the formula. Also works in reverse — paste a formula you inherited and ask *"Explain what this does step by step."* (Use ChatGPT if you want to upload the actual spreadsheet file.)

**11. Translate something.** If you work with Francophone grantees, paste your English draft and ask for a French translation. Tell it the context (formal email, survey question, etc.) so it gets the register right.

## Research applications

Using AI for research-specific tasks. These require more prompting skill — give AI enough context and be specific about what you want.

**12. Get a quick overview of a new topic.** When scoping a new intervention or investigation, ask AI to map the evidence landscape: key studies, direction of evidence, what's been studied and what hasn't. Use a tool with web search (Gemini, ChatGPT) for this, or turn on Deep Research mode. Verify everything it finds.

**13. Extract parameters from a paper.** When you need specific numbers for a CEA or BOTEC — effect sizes, baseline rates, costs — upload the paper and ask AI to find and report them with page references and confidence intervals. Faster than hunting through tables yourself, but always verify.

**14. Ask for pushback on your reasoning.** Write out your current thinking on an investigation or decision and ask AI to poke holes in it. *"What are the weakest points? What am I missing? Play devil's advocate."* This works best when you're specific about what you believe and why.

**15. Draft a check-in.** Give AI your raw thinking — what you've done, what you're finding, what you think so far — and ask it to structure this as a check-in with a bottom line, key reasons, uncertainties, and next steps. Good for organizing your thoughts before talking to your manager.

**16. Digest a long document quickly.** Upload an IR, CA, or long report and ask for the bottom line, key evidence, main uncertainties, and specific numbers you should know. Tell it how much time you have and what context you need it for (e.g., *"I have 15 minutes before a meeting about this grant"*).

**17. Use AI as a thought partner during an investigation.** Instead of a one-off question, have a back-and-forth conversation as you work through a problem. Share what you're finding, ask what you might be missing, and let it suggest angles to explore. This is where many people find the most value — not as a tool that produces output, but as a thinking partner that helps you reason.

**18. Interpret unfamiliar outcome measures.** When you encounter a metric you're not sure about — a biomarker level, a statistical measure, a unit conversion — ask AI to explain what it captures, what normal ranges are, and how it relates to the outcome you care about.

## Leveling up

These require more setup or prompting sophistication, but can save significant time.

**19. Edit your own writing for GiveWell legibility.** Paste a draft and ask AI to edit it for GiveWell's writing style: lead with a bottom line, use plain language, be specific with numbers, and be honest about uncertainty. This is especially useful for catch yourself writing in "academic mode." (See also Katie's [legibility project](https://claude.ai/project/019c0c02-0f9c-725b-9868-47fa06232618) in Claude — you can just paste text into it.)

**20. Set up a Claude Project for a recurring task.** If you work on a topic repeatedly (e.g., a specific pod area, a long-running investigation), create a Claude Project and upload key documents to it. Claude will use these as context in every conversation within that project — so you don't have to re-upload or re-explain each time. Google Docs attached to a project refresh automatically.

**21. Iterate on a prompt until the output is good.** Don't accept mediocre first outputs. Try: *"Focus more on X"*, *"That's not quite right because..."*, *"Make it shorter"*, *"Give me 2 more options."* Most good results come from 2-4 rounds of iteration, not a perfect first prompt.

**22. Try different tools for different tasks.** Use Gemini or ChatGPT when you need web search. Use ChatGPT when you need to work with a spreadsheet file. Use NotebookLM when you have a large collection of documents you'll reference repeatedly. Use Elicit for academic literature searches. See the Quick Start Guide for when to use what.

**23. Compare information across documents.** Upload two related documents (e.g., a CA and a grant page, or a grantee report and your IR) and ask AI to check for inconsistencies — factual differences, conflicting characterizations, or information in one that's missing from the other.

**24. Stress-test a grant recommendation.** Before finalizing a recommendation, share your case and key assumptions with AI and ask it to find the weakest points. *"Which assumptions are most fragile? What are the strongest arguments against this grant?"* Push it to be specific rather than generic.

**25. Synthesize information from multiple sources.** When you need to combine information from several documents into one coherent picture — e.g., creating a guidance doc from scattered notes, or pulling together what we know about an intervention from multiple CAs — upload everything and ask AI to synthesize by theme rather than by source.

**26. Generate questions for an interview or focus group.** Give AI the topic, goal, and audience, and ask for 10-15 open-ended questions grouped by theme. Good starting point that you can then refine based on your knowledge of the context.

**27. Build a reusable prompt for something you do repeatedly.** If you find yourself doing the same type of task often (e.g., summarizing a particular type of document, drafting a particular type of email), spend 15 minutes writing a detailed prompt with instructions, format, and an example of good output. Save it somewhere and reuse it. Share it in #ai-discussion if it's useful for others.

---

*Found something that works well? Share it with the team in #ai-discussion or send it to Brendan to add to the [Prompt Library](prompt-library.md).*
