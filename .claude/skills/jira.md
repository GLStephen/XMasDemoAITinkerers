---
name: jira
description: Create Jira tickets with correct fields and naming conventions
---

# Jira Ticket Creation

## Configuration

- **Project**: YOUR_PROJECT_KEY
- **Cloud ID**: your-org.atlassian.net
- **Required Epic Fields**: duedate, customfield_10080 (Account)
- **Account**: Your Account Name (id: X)
- **Story Points**: customfield_10025 (default: 1)

## Naming Conventions

### Epics
Format: `[Category]: [Epic Name] - [Number]`
Example: `Feature: User Authentication - 1`

### Stories/Tasks
Format: `[Name] - [Designator]`
Example: `Update API Configuration - 1.4`

Do NOT prefix with "Story" or "Task" - the issue type field handles that.

## Creating Epics

```
mcp__mcp-atlassian-api__createJiraIssue
  cloudId: your-org.atlassian.net
  projectKey: YOUR_PROJECT_KEY
  issueTypeName: Epic
  summary: "[Category]: [Epic Name] - [Number]"
  description: (goal, phase, dependencies)
  additional_fields: {"duedate": "YYYY-MM-DD", "customfield_10080": X}
```

Example: `Feature: Customer Registration and Login - 2`

## Creating Stories

```
mcp__mcp-atlassian-api__createJiraIssue
  cloudId: your-org.atlassian.net
  projectKey: YOUR_PROJECT_KEY
  issueTypeName: Story
  summary: "[Name] - X.X"
  description: (depends on, required by, tasks, acceptance criteria)
  additional_fields: {"parent": {"key": "PROJ-XXX"}, "customfield_10025": 1}
```

Default story points: 1 (override if spec indicates otherwise)

## Description Template

```markdown
**Depends On**: [Story references or "None"]
**Required By**: [Story references or "None"]

[Description paragraph]

## Tasks
- Task 1
- Task 2

## Acceptance Criteria
- Criterion 1
- Criterion 2
```

## Notes

- Use plain bullet points (`-` or `*`), NOT checkbox syntax - the MCP tool converts markdown to ADF and doesn't support checkboxes
- Acceptance Criteria field (customfield_10835) requires Atlassian Document Format - include in description instead
- Stories without Sprint field go to backlog automatically
- Link parent epic via `additional_fields.parent.key`
- **Issue links (Blocks/is blocked by) not supported** - MCP tool doesn't support `issuelinks` field; document dependencies in description text, add actual links manually in Jira if needed
