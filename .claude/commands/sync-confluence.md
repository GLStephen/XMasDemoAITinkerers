---
name: sync-confluence
description: Sync a local documentation folder to a designated Confluence parent page
---

# Confluence Documentation Sync (Single-Folder Ownership)

Sync a local docs folder to a designated Confluence parent page. Local files are the source of truth.

## Configuration

- **Cloud ID**: your-org.atlassian.net
- **Space**: YOUR_SPACE
- **Parent Folder ID**: YOUR_PARENT_PAGE_ID
- **Local Path**: docs/_confluence/
- **Config File**: .claude/confluence-sync.json (global settings only)
- **Per-file State**: Footer comment in each `.md` file

## Commands

### /sync-confluence init

Initialize sync configuration. Run this first to set up the connection between your local folder and Confluence.

**Process**:
1. Prompt for:
   - Confluence space key
   - Parent page ID
   - Local directory path (default: docs/_confluence)
2. Validate space and parent page exist via `mcp__mcp-atlassian-api__getConfluencePage`
3. Create `.claude/confluence-sync.json` config file with:
   - cloudId, spaceKey, spaceId
   - localPath, parentFolderId
4. Create `docs/_confluence/.gitkeep` if directory doesn't exist
5. Offer to run initial sync

**Example**:
```
> /sync-confluence init
Space key [DOCS]:
Parent page ID [12345678]:
Local directory [docs/_confluence]:

✓ Found space DOCS (spaceId: 98765)
✓ Verified parent page (title: "Documentation Root")
✓ Config saved to .claude/confluence-sync.json
? Run initial sync now? (y/n)
```

### /sync-confluence sync

Push local changes to Confluence. Creates or updates pages based on local file state.

**Process**:
1. Read config from `.claude/confluence-sync.json`
2. Walk directory tree depth-first starting from `localPath`
3. For each directory:
   a. **Ensure README.md exists** — if missing, auto-create with title = folder name (title-cased)
   b. **Sync README.md first** → get its pageId (this becomes parent for siblings)
   c. **Sync all other .md files** as children of the README's pageId
   d. **Recurse into subdirectories**, passing README's pageId as their parent
4. For root-level files (directly in `_confluence/`), use configured `parentPageId`
5. For each file:
   - **New file** (no pageId in footer) → CREATE page via `mcp__mcp-atlassian-api__createConfluencePage`, then append footer with new pageId
   - **Existing file** (has pageId) → UPDATE page via `mcp__mcp-atlassian-api__updateConfluencePage` with new parentId if needed, update `lastSyncedAt` in footer
6. Report results: X created, Y updated, Z READMEs auto-generated

**Hierarchy Rules**:
- Every subfolder's `README.md` becomes the **parent page** for sibling `.md` files in that folder
- Files in `_confluence/` root (no subfolder) → children of configured `parentPageId`
- Subfolders recurse: subfolder's README is child of parent folder's README
- Missing `README.md` in a subfolder → auto-created with title = folder name (title-cased)
- Sync order: README first, then siblings, then recurse into subdirectories
- Existing pages are **re-parented** (not recreated) to preserve comments, history, watchers

**Title Collision Handling**:
If two files would have the same title under the same parent, append sequential suffixes:
- First: "Overview"
- Second: "Overview (B)"
- Third: "Overview (C)"

**Example**:
```
> /sync-confluence sync

Syncing docs/_confluence → DOCS / 12345678

✓ Created: auth/README.md → "Authentication Overview" (pageId: 111111)
  → Footer added to local file
✓ Updated: compliance/GDPR.md → "GDPR Compliance" (pageId: 111112)
  → Footer updated with new timestamp

Summary: 1 created, 1 updated
```

### /sync-confluence status

Show current sync configuration and file status.

**Process**:
1. Read `.claude/confluence-sync.json`
2. Scan local directory for `.md` files
3. Parse footer comments to identify:
   - Synced files (have pageId in footer)
   - New files (no footer)
4. Display summary with counts

**Example**:
```
> /sync-confluence status

Confluence Sync Status
======================

Local: docs/_confluence/
Confluence: DOCS / 12345678
Cloud: your-org.atlassian.net

Files:
  ✓ 3 synced (have pageId in footer)
  + 1 new (no footer, will create on sync)

Run /sync-confluence sync to push changes.
```

## Technical Details

### Content Transformation
- Preserve markdown formatting (code blocks, tables, lists)
- Extract title from first `# Header` or use filename without .md
- Maintain folder hierarchy as Confluence page parent/child relationships
- Warn about unsupported features (local images - not uploadable via MCP)

### Error Handling
- **Invalid space**: Prompt to check space key or re-run init
- **Missing parent page**: Error and suggest re-init
- **Rate limit (120 req/min)**: Exponential backoff with retry
- **Network error**: Retry up to 3 times, then fail gracefully
- **Partial failure**: Save progress, report which pages succeeded/failed

### State Management

**Global config** (`.claude/confluence-sync.json`):
- Space and parent folder configuration only
- No per-file tracking

**Per-file state** (markdown comment at end of each `.md` file):
```markdown
[//]: # (confluence-sync: pageId=12345678, lastSyncedAt=2025-01-15T10:30:00.000Z)
```

**Footer handling**:
- Uses markdown link reference "comment" syntax
- Confluence automatically strips it during markdown→storage conversion
- No pre-processing needed - push file content as-is
- Invisible in both local markdown preview and Confluence
- Stays with the file through git operations

### Known Limitations
- **No delete API**: MCP doesn't support page deletion - remove pages manually in Confluence
- **No image upload**: Local images in markdown won't be uploaded (MCP limitation)
- **Rate limits**: Atlassian cloud typically limits to ~120 requests/minute
- **Sequential operations**: Pages created/updated one-by-one (no bulk API)
- **Always pushes**: No change detection - every sync pushes all files (Confluence handles versioning)

### Troubleshooting

**"A page with this title already exists" error**

This happens when a file's sync footer was removed but the page still exists in Confluence.

*Cause:* Without the `pageId` in the footer, sync treats the file as new and tries to create it.

*Recovery options:*
1. **Restore the footer** - Add back the sync comment with the correct pageId:
   ```markdown
   [//]: # (confluence-sync: pageId=XXXXXXX, lastSyncedAt=TIMESTAMP)
   ```
   Find the pageId from the Confluence page URL (the number in `/pages/XXXXXXX/`)

2. **Delete and recreate** - Remove the page from Confluence manually, then re-run sync to create it fresh

## Hierarchy Mapping

The filesystem structure maps directly to Confluence page hierarchy using README.md as parent pages:

```
docs/_confluence/
├── example.md                   → child of Parent Page (root-level file)
├── architecture/
│   ├── README.md                → "Architecture" (child of Parent Page)
│   ├── overview.md              → "Overview" (child of Architecture README)
│   ├── decisions.md             → "Decisions" (child of Architecture README)
│   └── diagrams/
│       ├── README.md            → "Diagrams" (child of Architecture README, auto-created if missing)
│       └── system-context.md    → "System Context" (child of Diagrams README)
└── guides/
    ├── README.md                → "Guides" (child of Parent Page)
    └── getting-started.md       → "Getting Started" (child of Guides README)
```

**Results in Confluence:**
```
Configured Parent Page (parentFolderId)
├── Example
├── Architecture
│   ├── Overview
│   ├── Decisions
│   └── Diagrams
│       └── System Context
└── Guides
    └── Getting Started
```

**Key rules:**
- `README.md` = parent page for its folder
- Other `.md` files = children of the README in same folder
- Subdirectories = their README becomes child of parent folder's README
- No `README.md` in subfolder = auto-create one titled after folder name
- Root `_confluence/` does NOT need a README — contents go directly under `parentFolderId`
