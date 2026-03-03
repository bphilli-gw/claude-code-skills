# Slack MCP Setup

This guide walks you through connecting Claude Code to Slack so it can read channels, search messages, and post on your behalf.

> **Note:** At GiveWell, the Slack MCP typically requires IT/Tech approval. If you can't get approval, skip this — most workflows work fine with Gmail + local files.

## What This Gives You

Once set up, Claude Code can:
- Read Slack channel messages
- Search across public (and optionally private) channels
- Read thread replies
- Send messages and schedule messages
- Look up user profiles

## Option A: Official Slack MCP (Simplest)

This uses Anthropic's official Slack integration via SSE (Server-Sent Events).

### Setup

```bash
claude mcp add --transport sse slack "https://mcp.slack.com/sse"
```

### Authorize

1. Restart Claude Code
2. It should prompt you to authorize via Slack OAuth in your browser
3. Sign in to your GiveWell Slack workspace and approve

### Verify

In Claude Code, ask:
```
Read the last 10 messages from #ai-discussion
```

## Option B: Custom Slack App (If Option A is blocked)

If your organization blocks the official MCP, you can create a custom Slack app.

### Step 1: Create the App

1. Go to [api.slack.com/apps](https://api.slack.com/apps)
2. Click **Create New App > From manifest**
3. Select your workspace
4. Paste this manifest:

```json
{
  "display_information": {
    "name": "Claude Code Assistant"
  },
  "oauth_config": {
    "scopes": {
      "bot": [
        "channels:history",
        "channels:read",
        "groups:history",
        "groups:read",
        "im:history",
        "im:read",
        "users:read",
        "chat:write"
      ]
    }
  }
}
```

### Step 2: Install to Workspace

1. Go to **Install App** in your app settings
2. Click **Install to Workspace** (may require admin approval)
3. Copy the **Bot User OAuth Token** (starts with `xoxb-`)

### Step 3: Configure

Ask Brendan for help configuring this token with Claude Code — the setup varies depending on which MCP server implementation you use.

## Troubleshooting

**"Slack app not approved"**: Ask in #tech-support or contact Nicole B. about getting the app approved. Reference the AI Vanguard program.

**Can't access private channels**: The bot needs to be invited to each private channel you want it to read. Type `/invite @Claude Code Assistant` in the channel.

**Rate limiting**: If Slack returns errors during large searches, wait a minute and try again. Slack rate-limits API calls.

## If Slack Isn't Available

You can still get most of the value by:
1. Manually exporting important Slack threads as text files
2. Saving them in your project folder
3. Asking Claude Code to read them as local files
