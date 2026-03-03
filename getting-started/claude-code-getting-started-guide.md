# Getting Started with Claude Code — for GiveWell researchers

Claude Code is a command-line tool that lets you work with Claude directly from your terminal. Unlike the web chat interface, Claude Code can read and write files on your computer, run commands, and maintain project context across chats. You can think of it as a souped-up version of Claude projects with better ability to reference large amounts of context while being “smarter”, particularly on more complex tasks by not short-changing the amount of tokens it uses to complete a task. 

**You do not need to know how to code to use Claude Code.** You interact with it in plain English. This guide will get you set up and give a few tips to get started.

**Note:** As of February 16th, [Nicole Bouchard](mailto:nicole.bouchard@givewell.org) will need to approve you to have a Claude Code account before you can get one connected to your GiveWell Claude account. 

[Part 1: Setup](#part-1:-setup)

[Choose your IDE](#choose-your-ide)

[A note on authentication](#a-note-on-authentication)

[A note on permissions](#a-note-on-permissions)

[Part 2: Tips for Initial Use and Project Setup](#part-2:-tips-for-initial-use-and-project-setup)

[Getting oriented](#getting-oriented)

[Start every project with a CLAUDE.md file](#start-every-project-with-a-claude.md-file)

[Feed Claude rich context](#feed-claude-rich-context)

[Use the plan-first workflow](#use-the-plan-first-workflow)

[Manage context window length](#manage-context-window-length)

[Know what Claude Code is good (and bad) at](#know-what-claude-code-is-good-\(and-bad\)-at)

[Useful commands reference](#useful-commands-reference)

[Further reading](#further-reading)

# Part 1: Setup {#part-1:-setup}

You'll need two things: an IDE (the application you'll work in) and Claude Code itself (installed inside that IDE's terminal).

## Choose your IDE {#choose-your-ide}

The most common options are [Cursor](https://cursor.com) and [VS code](https://code.visualstudio.com). I (Brendan) use VS code, but I don’t think there’s a significant difference so pick whichever appeals to you. 

### Option A: Cursor

Cursor is a polished IDE with a built-in AI chat pane and good defaults for non-technical users. For detailed instructions, see [this guide](https://hannahstulberg.substack.com/p/claude-code-for-everything-finally).

**Quick summary:**

1. Go to [cursor.com](https://cursor.com) and download the installer for your OS.  
2. Open Cursor. Click "Open Project" and select (or create) a folder where your project will live — e.g., a folder called `my-research-project` on your Desktop or in a cloud storage folder (Dropbox, Google Drive, OneDrive).  
3. Open the terminal inside Cursor: look for a panel at the bottom of the window, or use the menu `View > Terminal`, or press ``` Ctrl+`` ```  on your keyboard.  
4. Install Claude Code by pasting this into the terminal and pressing Enter:  
   - **Mac/Linux:** `curl -fsSL https://claude.ai/install.sh | bash`  
   - **Windows:** `irm https://claude.ai/install.ps1 | iex`  
5. Type `claude` and press Enter. Follow the login prompts to authenticate with your Anthropic account. (Use your **Anthropic account**, not a console account or API credits.)  
6. You should see the Claude Code interface. You're ready.

### Option B: VS Code

VS Code is a free, widely used IDE from Microsoft. For a video walkthrough of this path, see Brendan's setup video (link in footnote).[^1]

* **Note:** I put that video together when we were using a console account, see [this note](#a-note-on-authentication) on authenticating your account. 

**Quick summary:**

1. Go to [code.visualstudio.com](https://code.visualstudio.com) and download it. **Important:** Download "Visual Studio *Code*," not "Visual Studio" — they are different products.  
2. Install and open VS Code. Open a new folder for your project (`File > Open Folder`), or create one first.  
3. Open a new terminal: `Terminal > New Terminal` from the top menu.  
4. Install Claude Code by pasting the appropriate command (see Step 4 under Cursor above).  
5. Type `claude` and press Enter. Authenticate with your **Anthropic Console account**.  
6. You're set up.

## A note on authentication {#a-note-on-authentication}

GiveWell's account is set up as an enterprise account. When Claude Code asks you to log in, choose "Sign in with your Anthropic account." This will open a browser window for authorization and you should sign in with your GiveWell account.

## A note on permissions {#a-note-on-permissions}

Claude Code asks your permission before it takes actions (creating files, running commands, etc.). This is a safety feature.

Typically, you will:

- Press **1** to approve a single action.  
- Press **2** to approve all actions of that type for the current session (recommended — it reduces interruptions).

You can also pre-allow common safe commands by asking Claude: *"Help me set up my permissions so you can read files and run safe bash commands without asking. Walk me through /permissions."*

# Part 2: Tips for Initial Use and Project Setup {#part-2:-tips-for-initial-use-and-project-setup}

## Getting oriented {#getting-oriented}

When Claude Code starts, you'll see a text prompt at the bottom of the terminal. Just type what you want in plain English and press Enter. Claude will respond, ask follow-up questions, and take actions (creating files, editing documents, etc.) as needed.

Claude Code operates within a project folder (the folder you opened it in). It will not work unless you’ve selected a folder and you can make multiple projects each with their own instructions and context. 

I maintain a bunch of separate folders each for different projects and switch between them as needed within my Documents folder like so:

```
... DOCUMENTS/qea-writer
... DOCUMENTS/AI-planner
... DOCUMENTS/literature-tracker
```

## Start every project with a CLAUDE.md file {#start-every-project-with-a-claude.md-file}

This is the highest-leverage thing you can do to make Claude persistently useful across chats. A `CLAUDE.md` file sits in your project folder and acts as Claude's persistent memory — it reads this file at the start of every session. Without it, Claude starts fresh every time and you'll repeat yourself constantly.

**The easiest way to create one:** ask Claude to help you set up the project as the first thing you do in a new project. A good opening prompt when starting a new project:

```
"I'd like your help setting up this project. You'll be helping me with [describe the work — e.g., reviewing academic literature on malaria prevention, analyzing cost-effectiveness data, drafting a grant page]. I'll be providing [templates for you to follow, relevant academic studies, internal GiveWell research documents] and asking you to produce [grant pages, research reports]. Please propose a CLAUDE.md file with project instructions and a file structure to organize our work."
```

Claude will propose a structure, create folders and template files, and set up a `CLAUDE.md` that carries context across sessions. This is the workflow from the setup video — let Claude scaffold the project before you dive into the actual work.

**Alternatively,** run `/init` in Claude Code. It will analyze your project folder and generate a starter `CLAUDE.md`. Then you can review and refine it.

**What to include in your CLAUDE.md:**

- A brief description of the project and its purpose  
- The type of work Claude will be doing (research review, data analysis, document drafting, etc.)  
- Key constraints or standards (style guides, legibility guidance, page limits, )  
- File organization conventions  
- Any domain-specific terminology Claude should understand  
- Consider using my [standard prompt guidance](https://docs.google.com/document/d/1R589GtPZu-ACmyfWuQnviWSKhovcn2FyiZmv4rT3JP8/edit?tab=t.0#heading=h.2935zy8z275h) if you want to write your own Claude.md

Keep it concise. The official [Anthropic guidance](https://claude.com/blog/using-claude-md-files) says to think of it as onboarding a new team member: cover the *what*, *why*, and *how* of your project, but don't overload it.

## Feed Claude rich context {#feed-claude-rich-context}

Claude Code works with files on your computer, which is its superpower for research. Before asking Claude to do substantive work, give it as much relevant material to work with as you have:

- **Drop files into your project folder.** PDFs, Word docs, spreadsheets, text files — put them in the folder and Claude can read them.   
- **Drag and drop into the terminal.** You can drag a file directly into the Claude Code terminal to have Claude read it immediately.  
- **Be explicit about what to read.** Say things like *"Read @literature-review.pdf and summarize the key findings relevant to our cost-effectiveness model."*

Claude Code excels at tasks that involve following rules and executing structured workflows (data cleaning, running analyses, summarizing papers, generating reports) more than interpretation or novel argumentation. Give it the source material and clear instructions; reserve judgment and interpretation for yourself.

## Use the plan-first workflow {#use-the-plan-first-workflow}

When asking for a complex task, don't jump straight to asking Claude to produce a final output. The most effective workflow is:

1. **Ask Claude to plan first.** *"I want to draft a QEA on \[intervention\]. Before writing anything, outline the structure you'd use and what information you'd need from me."*  
2. **Review and refine the plan.** Correct misunderstandings, add constraints, point Claude to relevant files.  
3. **Then execute.** *"This plan looks good. Go ahead and create the first draft."*  
4. **Iterate.** *"The section on cost-effectiveness needs to incorporate the data from @cea-model.xlsx. Revise it."*

This mirrors advice from Anthropic's official best practices: Claude should understand the full scope before it starts writing. You can also use this prompt pattern from the docs:

*"I want to build \[brief description\]. Interview me about the details — ask about scope, edge cases, and tradeoffs. Keep asking until we've covered everything, then write a plan to PLAN.md."*

## Manage context window length {#manage-context-window-length}

Claude Code has a limited "context window" — the amount of information it can hold in its working memory during a session. As conversations get long, Claude's effectiveness degrades. This is the most common source of quality problems.

Practical rules of thumb:

- **One task per session.** When you finish a major task, use `/clear` to reset the conversation or start a new Claude Code session.   
  - Often, you’ll want to ask Claude to update your `CLAUDE.md` before starting a new chat since it persists across chats.  
- **Save important outputs to files.** Ask Claude to write plans, summaries, and intermediate results to markdown files in your project folder. Files survive session resets; conversation history doesn't.  
- **Break big projects into steps.** Instead of "Write me a complete literature review," try: "Read these 5 papers and create a summary table in `lit-review-summaries.md`," then in a new session: "Using @lit-review-summaries.md, draft the literature review section."  
- **Watch the context indicator.** At the bottom of the terminal, you'll see a bar showing how much context you've used. When it gets high, consider starting fresh.

## Know what Claude Code is good (and bad) at {#know-what-claude-code-is-good-(and-bad)-at}

Based on the experience of researchers using Claude Code for empirical and policy work:

**Strong use cases:**

- Structuring and drafting documents from source materials (grant pages, investigation plans, reports)  
- Data cleaning, transformation, and analysis (give it a CSV and an analysis plan)  
- Literature organization and summarization  
- Converting between formats (e.g., Excel models to Python, drafts to presentation slides)  
- Creating visualizations and tables from data  
- Automating repetitive document processing

**More limited:**

- **Interpretation of results.** Claude will interpret statistical output or research findings if you let it, but these interpretations can be unreliable.  
- **Citations and literature claims.** Claude can hallucinate references that look plausible but don't exist. Verify citations against the actual source material.  
- **Novel argumentation.** Claude is following patterns, not reasoning from first principles about your specific policy question. Use it to structure and draft; supply the analytical judgment yourself.

## Useful commands reference {#useful-commands-reference}

| Command | What it does |
| :---- | :---- |
| `claude` | Start Claude Code |
| `claude --dangerously-skip-permissions` | Start without permission prompts |
| `claude --continue` | Resume your last session |
| `claude --resume` | Pick a past session to resume |
| `/init` | Generate a starter CLAUDE.md |
| `/clear` | Clear conversation history (keeps CLAUDE.md) |
| `/permissions` | Manage what Claude can do without asking |
| `@filename` | Reference a specific file in your prompt |
| `Shift+Tab` | Cycle between permission modes |
| `Esc` | Stop Claude mid-action |

## Further reading {#further-reading}

- [Hannah Stulberg's full Claude Code setup guide](https://hannahstulberg.substack.com/p/claude-code-for-everything-finally) — detailed, screenshot-rich, aimed at non-coders (also covers Markdown basics and bash commands)  
- [Anthropic's official best practices](https://code.claude.com/docs/en/best-practices) — the source-of-truth reference  
- [Anthropic's guide to CLAUDE.md files](https://claude.com/blog/using-claude-md-files) — how to structure project memory  
- [Scott Cunningham's Claude Code for Empirical Research series](https://causalinf.substack.com/p/claude-code-part-12-how-i-use-claude) — an economist's workflow for quantitative social science  
- [Tom Pepinsky on Agentic AI and Social Science](https://tompepinsky.com/2026/01/23/agentic-ai-and-social-science-research-practice/) — clear-eyed assessment of strengths and limits for research
- [The Complete Guide to Building Skills for Claude (PDF)](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf?hsLang=en) — Anthropic's 32-page guide to "Skills," a way to package reusable workflows and instructions that Claude loads automatically. Not essential now, but relevant once you're ready to share repeatable prompts or workflows across the team.

[^1]:  [https://us06web.zoom.us/rec/share/znov7D0f9jqtD8SF7HshMFPrGfik3djr8rO\_COyd33SU29eCferO4bHVQmFOIPTp.WOA1eUtds4BvKqUB?startTime=1766435068000](https://us06web.zoom.us/rec/share/znov7D0f9jqtD8SF7HshMFPrGfik3djr8rO_COyd33SU29eCferO4bHVQmFOIPTp.WOA1eUtds4BvKqUB?startTime=1766435068000)