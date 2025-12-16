# Jira Integration

## What It Does

The Jira integration allows teams to define epics and stories in markdown format, then have Claude automatically create properly formatted Jira tickets.

## Business Value

- **Consistency** - Every ticket follows project naming conventions
- **Speed** - Create multiple tickets in seconds, not minutes
- **Accuracy** - Required fields always populated correctly
- **Traceability** - Epic-to-story hierarchy maintained

## How It Works

1. Team writes epic specification in markdown
2. Specification includes stories with acceptance criteria
3. Claude reads the spec and creates Jira tickets
4. Tickets are linked (epic → stories) automatically
5. Custom fields (story points, accounts) are set

## Example Workflow

**Before (Manual):**
- Open Jira
- Create epic, fill 8 fields
- Create story, fill 10 fields, link to epic
- Repeat for each story
- ~5 minutes per ticket

**After (AI-Assisted):**
- Write epic spec in markdown
- Ask Claude to create tickets
- Review and approve
- ~30 seconds per ticket

## Supported Features

| Feature | Supported |
|---------|-----------|
| Epic creation | Yes |
| Story creation | Yes |
| Task creation | Yes |
| Parent linking | Yes |
| Story points | Yes |
| Custom fields | Yes |
| Sprint assignment | Manual |
| Attachments | No |

## Getting Started

Epics are defined in the `_sprints/` folder. See the sprint folders for examples of epic specifications that can be processed by Claude.
