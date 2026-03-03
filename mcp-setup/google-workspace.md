# Google Workspace MCP Setup

This guide walks you through connecting Claude Code to Gmail, Google Drive, Docs, Calendar, and Sheets via the Google Workspace MCP server.

## What This Gives You

Once set up, Claude Code can:
- Search and read Gmail messages
- Read files from Google Drive
- Read Google Docs content
- Check your Google Calendar
- Read Google Sheets data

This is added at **user scope**, meaning it works across all your Claude Code projects — you only set it up once.

## Prerequisites

- Claude Code installed
- Python 3.10+ installed
- [uv](https://docs.astral.sh/uv/) installed (`pip install uv` or `brew install uv`)
- A Google account (your GiveWell account)

## Step 1: Create a Google Cloud Project

1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Click "Select a project" at the top, then "New Project"
3. Name it something like "Claude Code MCP"
4. Click "Create"

## Step 2: Enable APIs

1. In your new project, go to **APIs & Services > Library**
2. Search for and enable each of these:
   - Gmail API
   - Google Drive API
   - Google Calendar API
   - Google Docs API
   - Google Sheets API

## Step 3: Configure OAuth Consent Screen

1. Go to **APIs & Services > OAuth consent screen**
2. Choose **Internal** (if using a work Google account) or **External** (personal)
3. Fill in:
   - App name: "Claude Code"
   - Support email: your email
   - Developer email: your email
4. Add scopes:
   - `https://www.googleapis.com/auth/gmail.readonly`
   - `https://www.googleapis.com/auth/drive.readonly`
   - `https://www.googleapis.com/auth/calendar`
   - `https://www.googleapis.com/auth/documents.readonly`
   - `https://www.googleapis.com/auth/spreadsheets.readonly`

## Step 4: Create OAuth Credentials

1. Go to **APIs & Services > Credentials**
2. Click **Create Credentials > OAuth client ID**
3. Application type: **Desktop app**
4. Note the **Client ID** and **Client Secret** — you'll need these in the next step

## Step 5: Clone the MCP Server

```bash
cd ~
git clone <your-workspace-mcp-repo> hardened-google-workspace-mcp
```

> Ask Brendan for the repo URL if you don't have it.

## Step 6: Add MCP Server to Claude Code

Run this in your terminal (replace the placeholder values):

```bash
claude mcp add hardened-workspace \
  --scope user \
  -e GOOGLE_OAUTH_CLIENT_ID="YOUR_CLIENT_ID_HERE" \
  -e GOOGLE_OAUTH_CLIENT_SECRET="YOUR_CLIENT_SECRET_HERE" \
  -- uv run --directory ~/hardened-google-workspace-mcp python -m main --single-user
```

## Step 7: Authorize

1. Restart Claude Code (close and reopen your terminal, then run `claude`)
2. It should open a browser window for Google OAuth
3. Sign in with your Google account and authorize access

## Step 8: Verify

In Claude Code, ask:
```
Search my recent Gmail for messages about [topic]
```

If it works, you're all set. If not, try:
```bash
# Check MCP status
claude mcp list

# Should show: hardened-workspace: Connected
```

## Troubleshooting

**"MCP Connection Failed"**: Remove and re-add the server:
```bash
claude mcp remove hardened-workspace --scope user
# Then re-run the add command from Step 6
```

**"OAuth Token Expired"**: The server handles token refresh automatically. If auth fails, remove and re-add the MCP server to re-trigger OAuth.

**"API not enabled"**: Go back to Step 2 and make sure all APIs are enabled in your Google Cloud project.
