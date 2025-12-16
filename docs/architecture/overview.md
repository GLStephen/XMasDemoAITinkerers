# System Architecture

## Overview

This project demonstrates AI-assisted development workflows using Claude Code with MCP (Model Context Protocol) integrations.

## Components

```
┌─────────────────────────────────────────────────────────────┐
│                      Claude Code CLI                         │
├─────────────────────────────────────────────────────────────┤
│  Skills          │  Commands        │  CLAUDE.md Context    │
│  (Always-on)     │  (Invokable)     │  (Project rules)      │
├──────────────────┴──────────────────┴───────────────────────┤
│                    MCP Tool Layer                            │
├─────────────────────────────────────────────────────────────┤
│  Atlassian API   │  File System     │  Other MCPs           │
│  (Jira/Conflu)   │  (Read/Write)    │  (Extensible)         │
└─────────────────────────────────────────────────────────────┘
```

## Key Integrations

### Jira (via MCP)
- Create epics, stories, and tasks
- Follow project-specific naming conventions
- Link parent/child relationships

### Confluence (via MCP)
- Sync local markdown to Confluence pages
- Maintain hierarchy through README.md conventions
- Track sync state via footer comments

## Directory Conventions

| Pattern | Purpose |
|---------|---------|
| `_confluence/` | Content destined for Confluence sync |
| `_sprints/` | Sprint planning content for Jira |
| `_inbox/` | Unprocessed incoming items |
| `demos/` | Sprint demo summaries |
