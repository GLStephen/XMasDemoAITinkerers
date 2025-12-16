# Confluence Sync

## Overview

The `/sync-confluence` command synchronizes local markdown files to Confluence pages, maintaining hierarchy and tracking state.

## Location

```
.claude/commands/sync-confluence.md
```

## Commands

| Command | Purpose |
|---------|---------|
| `/sync-confluence init` | Configure space and parent page |
| `/sync-confluence sync` | Push local changes to Confluence |
| `/sync-confluence status` | Show sync state and pending changes |

## Hierarchy Mapping

Local folder structure maps to Confluence page hierarchy:

```
_confluence/
├── README.md           → Parent page
├── overview.md         → Child of parent
└── section/
    ├── README.md       → Child of parent, parent of section
    └── detail.md       → Child of section README
```

## State Tracking

### Global Config
`.claude/confluence-sync.json`:
```json
{
  "cloudId": "your-org.atlassian.net",
  "spaceKey": "DOCS",
  "parentPageId": "12345678",
  "localPath": "docs/_confluence"
}
```

### Per-File State
Footer comment in each synced file:
```markdown
[//]: # (confluence-sync: pageId=12345678, lastSyncedAt=2025-01-15T10:30:00.000Z)
```

## Content Transformation

| Markdown | Confluence |
|----------|------------|
| `# Heading` | Page title |
| Code blocks | Confluence code macro |
| Tables | Confluence tables |
| Lists | Native lists |

## Limitations

- No image upload (MCP limitation)
- No page deletion (manual only)
- No checkbox syntax (use plain bullets)
- Sequential operations (no bulk API)
