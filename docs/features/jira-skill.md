# Jira Skill

## Overview

The Jira skill provides Claude with context about how to create Jira tickets following project conventions.

## Location

```
.claude/skills/jira.md
```

## How It Works

The skill is referenced in `CLAUDE.md` using the `@` directive:
```markdown
@.claude/skills/jira.md
```

This makes the skill content available to Claude automatically when working in this repository.

## Capabilities

### Epic Creation
```
mcp__mcp-atlassian-api__createJiraIssue
  issueTypeName: Epic
  summary: "[Category]: [Epic Name] - [Number]"
  additional_fields: {"duedate": "YYYY-MM-DD", "customfield_10080": X}
```

### Story Creation
```
mcp__mcp-atlassian-api__createJiraIssue
  issueTypeName: Story
  summary: "[Name] - X.X"
  additional_fields: {"parent": {"key": "PROJ-XXX"}, "customfield_10025": 1}
```

## Naming Conventions

| Type | Format | Example |
|------|--------|---------|
| Epic | `[Category]: [Name] - [Number]` | `Feature: User Auth - 1` |
| Story | `[Name] - [Designator]` | `Login Form - 1.1` |
| Task | `[Name] - [Designator]` | `Add validation - 1.1.1` |

## Custom Fields

| Field | ID | Purpose |
|-------|-----|---------|
| Account | customfield_10080 | Billing/cost tracking |
| Story Points | customfield_10025 | Estimation |

## Usage with _sprints/

Epic files in `_sprints/` follow a structure that the Jira skill can process:

```markdown
# Epic: Feature Name

**Category**: Feature
**Number**: 1
**Due Date**: 2025-01-15

## Description
[Epic description]

## Stories

### Story 1.1: First Story
[Story description and acceptance criteria]

### Story 1.2: Second Story
[Story description and acceptance criteria]
```
