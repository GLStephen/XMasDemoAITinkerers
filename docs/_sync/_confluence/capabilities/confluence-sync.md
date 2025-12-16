# Confluence Sync

## What It Does

Confluence Sync keeps business documentation current by automatically pushing markdown files to Confluence pages.

## Business Value

- **Single source of truth** - Edit in one place, publish everywhere
- **Always current** - No more outdated Confluence pages
- **Developer-friendly** - Write in markdown, not Confluence editor
- **Version controlled** - Documentation changes tracked in git

## How It Works

1. Documentation written in `_sync/_confluence/` folder
2. Run `/sync-confluence sync` command
3. Claude pushes changes to Confluence
4. Page hierarchy matches folder structure
5. Footer tracks sync state for future updates

## Example Workflow

**Before (Manual):**
- Write doc in markdown
- Copy to Confluence
- Format using Confluence editor
- Repeat when changes needed
- Eventually goes stale

**After (Automated):**
- Write doc in markdown
- Run sync command
- Documentation stays current
- Changes are version controlled

## Supported Features

| Feature | Supported |
|---------|-----------|
| Create pages | Yes |
| Update pages | Yes |
| Page hierarchy | Yes |
| Code blocks | Yes |
| Tables | Yes |
| Delete pages | Manual only |
| Images | Manual only |

## Use Cases

- Project status pages
- Technical documentation summaries
- Sprint demo notes
- Meeting summaries
- FAQ and glossaries

## Getting Started

Documentation destined for Confluence lives in `docs/_sync/_confluence/`. The folder structure becomes the page hierarchy in Confluence.
