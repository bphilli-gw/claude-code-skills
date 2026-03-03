# Examples

These are full production workflows from real Claude Code projects at GiveWell. They're here for learning and inspiration — **read them to understand the patterns, but don't copy them directly** into your project (they depend on project-specific context that won't exist in yours).

Start with each example's `ABOUT.md` for an overview of what it demonstrates and which patterns are worth reusing.

## Examples

### [Grant Page Workflow](grant-page-workflow/)
A 6-stage pipeline for drafting GiveWell grant pages from Conditional Approvals. Demonstrates multi-stage workflows with checkpoints, hard rules embedded in commands, and context calibration from example documents.

**Key patterns**: Stage-gated workflow, hard rules in every command, context folder with examples.

### [Literature Tracker Skills](literature-tracker-skills/)
A composable skills architecture for producing QEAs, BOTECs, and research reports. Demonstrates how to build small, reusable skills and orchestrate them with commands, plus the Write-Review-Revise loop for quality control.

**Key patterns**: Composable skills, writer/reviewer pairs, anti-rubber-stamp review protocol.

### [Project Manager Workflow](project-manager-workflow/)
A multi-source intelligence aggregation system that pulls from Slack, Gmail, Google Docs, and local files to produce weekly project briefs. Demonstrates MCP server integration and per-project configuration.

**Key patterns**: MCP integration, per-project config, raw data preservation, multi-source synthesis.
