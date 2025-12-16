# Documentation Hub

This repository demonstrates Claude Code features and AI-assisted development workflows.

## Structure

| Folder | Purpose | Audience |
|--------|---------|----------|
| `architecture/` | System design and technical decisions | Developers |
| `features/` | Feature specifications and implementation details | Developers |
| `guides/` | How-to guides and tutorials | All users |
| `_sync/_confluence/` | Business summaries synced to Confluence | Stakeholders |
| `_sprints/` | Sprint planning with epics and stories | Product/Dev team |
| `_inbox/` | Incoming items awaiting processing | All |

## Workflows

### Technical Documentation
Source of truth lives in `architecture/`, `features/`, and `guides/`. These are developer-focused with code examples and implementation details.

### Business Documentation (_sync/_confluence/)
Summaries and status updates for stakeholders. Uses the `/sync-confluence` command to push to Confluence. The `_sync/` folder can accommodate other sync destinations in the future. See [Confluence Sync](features/confluence-sync.md).

### Sprint Planning (_sprints/)
Epics and stories defined in markdown. Uses the Jira skill to create tickets. Each sprint includes a `demos/` folder documenting what's ready to show clients.

### Incoming Items (_inbox/)
Raw meeting notes, feature requests, and feedback. Items here get triaged into either `_sprints/` (for planned work) or `_sync/_confluence/` (for documentation).
