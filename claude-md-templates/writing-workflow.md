# [Document Type] Writer

## Purpose

[What document does this project produce? E.g., grant pages, investigation plans, reports.]
Claude's role: draft documents from source materials following defined quality standards.

## Workflow

[Describe the stages. Example:]

| Stage | What happens | Output |
|-------|-------------|--------|
| 0. Assess | Check if inputs are ready | Readiness report |
| 1. Extract | Pull key information from sources | Structured notes |
| 2. Plan | Outline the document structure | Section plan |
| 3. Draft | Write each section | Full draft |
| 4. Review | Quality-check against standards | QC report |
| 5. Finalize | Apply fixes, format for delivery | Final document |

## Source Materials

```
project-name/
├── CLAUDE.md
├── input/                 # Source documents to draft from
├── context/               # Style guides, templates, examples
│   ├── template.md        # The template to follow
│   ├── style-guide.md     # Writing conventions
│   └── examples/          # Good examples of the output
├── output/                # Drafts and final documents
└── .claude/
    └── commands/          # Stage commands (if using multi-stage workflow)
```

## Hard Rules

These are non-negotiable constraints. Violating any of these is a blocking issue.

- **Source discipline**: Only use information from provided source documents. Never fabricate facts, quotes, or statistics.
- **Numeric precision**: All numbers must exactly match the source. Include units, time periods, and any qualifiers from the original.
- **Template adherence**: Follow the document template structure exactly. Do not add, remove, or rename sections.
- **Style compliance**: Follow the style guide in `context/`. See the [GiveWell style guide](../reference/givewell-style-guide.md).
- **No sensitivity violations**: [Define what's off-limits — e.g., internal deliberations, individual staff opinions, unpublished data.]

## Quality Standards

[Define what "good" looks like for this document type. Examples:]

- Every claim is traceable to a source document
- The document reads naturally — not like a template was filled in
- Numbers are correct and appropriately contextualized
- Uncertainty is stated honestly
- A reader unfamiliar with the topic can understand the bottom line within 30 seconds
