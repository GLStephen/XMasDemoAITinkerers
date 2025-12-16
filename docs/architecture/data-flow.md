# Data Flow

## Documentation Workflow

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   _inbox/    │────▶│  Triage &    │────▶│  _sprints/   │
│  (raw input) │     │  Process     │     │  (planned)   │
└──────────────┘     └──────────────┘     └──────────────┘
                            │
                            ▼
                     ┌──────────────┐     ┌──────────────┐
                     │ _confluence/ │────▶│  Confluence  │
                     │ (summaries)  │     │  (external)  │
                     └──────────────┘     └──────────────┘
```

## Sprint Planning Flow

```
1. Epic defined in _sprints/sprint-XX/epic-*.md
                    │
                    ▼
2. Claude reads epic, uses Jira skill
                    │
                    ▼
3. Jira tickets created with correct hierarchy
                    │
                    ▼
4. Demo summary added to _sprints/sprint-XX/demos/
```

## Confluence Sync Flow

```
1. Markdown files in _confluence/
                    │
                    ▼
2. /sync-confluence command invoked
                    │
                    ▼
3. Files walked depth-first
   - README.md becomes parent page
   - Other .md files become children
                    │
                    ▼
4. MCP creates/updates Confluence pages
                    │
                    ▼
5. Footer comment added with pageId
   [//]: # (confluence-sync: pageId=XXX, lastSyncedAt=...)
```

## State Management

| Location | State Stored |
|----------|--------------|
| `.claude/confluence-sync.json` | Sync configuration |
| File footer comments | Per-file page IDs |
| Jira | Ticket status, assignments |
| Confluence | Page versions, comments |
