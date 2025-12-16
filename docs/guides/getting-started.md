# Getting Started

## Prerequisites

- Claude Code CLI installed
- Access to Atlassian Cloud (Jira/Confluence)
- MCP Atlassian API configured

## Quick Start

### 1. Clone the Repository

```bash
git clone <repository-url>
cd XMasDemoAITinkerers
```

### 2. Review Project Structure

```
.claude/
  skills/jira.md          # Jira ticket conventions
  commands/sync-confluence.md  # Confluence sync command
CLAUDE.md                 # Project context
docs/                     # Documentation hub
```

### 3. Try the Workflows

**Create a Jira ticket:**
Open an epic file in `docs/_sprints/` and ask Claude to create the tickets.

**Sync to Confluence:**
```
/sync-confluence init
/sync-confluence sync
```

**Process inbox items:**
Review items in `docs/_inbox/` and ask Claude to triage them.

## Common Tasks

| Task | How |
|------|-----|
| Create Jira epic | "Create Jira tickets from this epic file" |
| Sync docs | `/sync-confluence sync` |
| Check sync status | `/sync-confluence status` |
| Plan a sprint | "Help me plan sprint 3 based on the backlog" |
| Summarize for business | "Create a business summary of this feature for Confluence" |

## Next Steps

- Read [Installation](installation.md) for detailed setup
- Review [Architecture Overview](../architecture/overview.md)
- Check [Troubleshooting](troubleshooting.md) if you hit issues
