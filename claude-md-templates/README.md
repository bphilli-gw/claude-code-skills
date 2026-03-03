# CLAUDE.md Templates

## What Is a CLAUDE.md?

A `CLAUDE.md` file sits at the root of your project folder and acts as Claude's persistent memory. Claude reads it at the start of every session, so it always knows your project's purpose, rules, and file structure without you repeating yourself.

**This is the highest-leverage thing you can do** to make Claude consistently useful. Without it, Claude starts fresh every conversation.

## How to Use These Templates

1. Pick the template closest to your use case
2. Copy it to your project folder as `CLAUDE.md`
3. Fill in the `[bracketed]` sections with your project specifics
4. Iterate — ask Claude to help you refine it as you learn what works

```bash
cp claude-md-templates/research-project.md your-project/CLAUDE.md
```

## Which Template Should I Use?

| Template | Best for | Complexity |
|----------|---------|-----------|
| **[Simple](simple-project.md)** | Quick tasks, one-off analyses, ad hoc projects | Minimal — just purpose, context, and file structure |
| **[Research](research-project.md)** | Investigations, literature reviews, data analysis | Moderate — includes source discipline rules and research-specific structure |
| **[Writing workflow](writing-workflow.md)** | Multi-stage document production (grant pages, reports) | Detailed — includes stages, hard rules, and quality standards |
| **[Knowledge base](knowledge-base.md)** | "Second brain" projects with accumulated context | Detailed — includes knowledge navigation, documentation support, and maintenance rules |

## Tips

- **Start simple, add complexity later.** The simple template is fine for most projects. Add sections as you discover what Claude needs to know.
- **Keep it concise.** A 50-line CLAUDE.md that Claude actually reads is better than a 500-line one it skims. Think "onboarding a new team member," not "writing a manual."
- **Update it as you go.** At the end of a session, ask Claude: "Is there anything we learned today that should go in the CLAUDE.md?" Then update it before your next session.
