# Example: Project Intelligence Hub

## What This Is

A Claude Code project that aggregates communications from Slack, Gmail, Google Docs, and local files to produce weekly project intelligence briefs. It uses MCP servers to connect to external services and follows a 6-stage pipeline.

**Status**: Testing. Local files + Gmail working. Slack integration pending IT approval.

## Why It Works

1. **Multi-source data aggregation**: Instead of manually checking Slack, email, and shared docs, the system pulls everything into one place and synthesizes it.

2. **Per-project configuration**: Each project has its own `config.yaml` specifying which Slack channels, Gmail labels, and local folders to pull from. This makes it easy to add new projects.

3. **Stage pipeline with raw data preservation**: Raw data from each source is saved before synthesis. If something goes wrong in synthesis, you can always re-run from the raw data.

4. **Templated outputs**: Weekly overviews, to-do lists, and memory updates all follow consistent templates.

## Key Patterns to Reuse

- **MCP server setup**: The `SETUP.md` and `.mcp.json` patterns show how to configure Google Workspace and Slack integrations. See the `mcp-setup/` guides in the shared repo for standalone versions.
- **Per-project configuration**: The `config.yaml` pattern — one config file per project with sources, team members, and output settings — is useful for any multi-project system.
- **Stage pipeline with checkpoints**: Similar to the grant page writer, but for data aggregation rather than document production.
- **Raw data preservation**: Never modify source data. Save it, then synthesize from it.

## What's NOT Reusable (without modification)

- The specific stage commands are tightly coupled to this project's data flow (Slack → Gmail → local files → synthesis → overview → to-dos → memory → calendar).
- Team member assignment logic is specific to GiveWell's project structure.
- The MCP server configurations reference specific OAuth credentials and server URLs.

## Files in This Example

- `commands/weekly-sync.md` — The orchestrator that runs all stages
- `commands/stage-0-gather.md` — Pull data from all sources
- `commands/stage-1-synthesize.md` — Create unified activity log
- `commands/stage-2-overview.md` — Generate 3-page weekly brief
- `commands/stage-3-todos.md` — Extract and assign to-dos
- `commands/stage-4-memory.md` — Update project memory/decisions log
- `commands/stage-5-calendar.md` — Create calendar events and notifications
- `commands/add-project.md` — Set up a new project
- `commands/project-status.md` — Check configuration status
- `commands/ai-weekly-status.md` — AI-specific status report
