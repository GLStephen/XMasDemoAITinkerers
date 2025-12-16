# Installation Guide

## Step 1: Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

Verify installation:
```bash
claude --version
```

## Step 2: Configure MCP Atlassian API

### Get Atlassian API Token

1. Go to https://id.atlassian.com/manage-profile/security/api-tokens
2. Click "Create API token"
3. Name it (e.g., "Claude Code MCP")
4. Copy the token

### Configure MCP

Create or update `.claude/mcp.json`:

```json
{
  "servers": {
    "mcp-atlassian-api": {
      "command": "npx",
      "args": ["-y", "mcp-atlassian-api"],
      "env": {
        "ATLASSIAN_SITE": "your-org.atlassian.net",
        "ATLASSIAN_USER": "your-email@example.com",
        "ATLASSIAN_API_TOKEN": "your-api-token"
      }
    }
  }
}
```

## Step 3: Configure Project

### Update Jira Skill

Edit `.claude/skills/jira.md`:
- Set your project key
- Set your cloud ID
- Configure custom field IDs for your instance

### Initialize Confluence Sync

```
/sync-confluence init
```

Follow the prompts to configure:
- Space key
- Parent page ID
- Local directory path

## Step 4: Verify Setup

Test Jira connection:
```
Ask Claude: "Search for recent issues in project PROJ"
```

Test Confluence connection:
```
/sync-confluence status
```

## Environment Variables

| Variable | Purpose |
|----------|---------|
| `ATLASSIAN_SITE` | Your Atlassian cloud domain |
| `ATLASSIAN_USER` | Your Atlassian email |
| `ATLASSIAN_API_TOKEN` | API token for authentication |

## Troubleshooting

See [Troubleshooting Guide](troubleshooting.md) for common issues.
