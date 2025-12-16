# MCP Integration

## What is MCP?

Model Context Protocol (MCP) is a standard for connecting AI assistants to external tools and data sources. Claude Code uses MCP to interact with services like Jira and Confluence.

## Configured Tools

### mcp-atlassian-api

Provides access to Atlassian Cloud products.

**Jira Operations:**
```
mcp__mcp-atlassian-api__createJiraIssue
mcp__mcp-atlassian-api__getJiraIssue
mcp__mcp-atlassian-api__updateJiraIssue
mcp__mcp-atlassian-api__searchJira
```

**Confluence Operations:**
```
mcp__mcp-atlassian-api__createConfluencePage
mcp__mcp-atlassian-api__updateConfluencePage
mcp__mcp-atlassian-api__getConfluencePage
mcp__mcp-atlassian-api__searchConfluence
```

## Authentication

MCP tools authenticate via environment variables or config files. The Atlassian API typically uses:
- API tokens (recommended)
- OAuth 2.0 for user-context operations

## Error Handling

Common MCP errors and solutions:

| Error | Cause | Solution |
|-------|-------|----------|
| `401 Unauthorized` | Invalid/expired token | Refresh API token |
| `404 Not Found` | Wrong space/project key | Verify configuration |
| `429 Rate Limited` | Too many requests | Implement backoff |

## Adding New MCP Servers

1. Install the MCP server package
2. Configure in `.claude/mcp.json`
3. Add skills/commands that use the new tools
