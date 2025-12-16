# Frequently Asked Questions

## General

### What is this project?
A demonstration of AI-assisted development workflows using Claude Code with Jira and Confluence integrations.

### Who is this for?
Development teams looking to streamline their workflows, reduce manual overhead, and improve documentation practices.

### Do I need coding experience?
Basic familiarity with markdown and git is helpful. The AI assistance is designed to lower the barrier for common tasks.

## Jira Integration

### How do I create Jira tickets?
Write your epic/story specifications in markdown files under `_sprints/`, then ask Claude to create the tickets.

### Can Claude update existing tickets?
Yes, but this requires the ticket key. Claude can search for and update tickets.

### Why aren't my custom fields populated?
Custom field IDs are instance-specific. Check that the Jira skill has the correct field IDs for your Jira instance.

### Can Claude assign tickets to people?
Yes, if you provide the assignee information. The MCP tool supports setting assignees.

## Confluence Sync

### How do I sync my docs?
Run `/sync-confluence sync` in Claude Code. Make sure you've run `/sync-confluence init` first.

### Why is my page not appearing?
Check that:
1. The file is in `_sync/_confluence/`
2. The file has a `.md` extension
3. There are no errors during sync

### Can I sync images?
Not automatically. Images must be uploaded to Confluence manually, then referenced by URL.

### How do I delete a synced page?
Delete it manually in Confluence. The sync tool doesn't support deletions.

### What happens if I lose the sync footer?
The sync will try to create a new page, which may fail if a page with that title exists. Either restore the footer or delete the Confluence page.

## Workflow

### Where do new items go?
New items (meeting notes, requests, feedback) go in `_inbox/`. They get triaged into `_sprints/` or `_sync/_confluence/` during planning.

### How do I plan a sprint?
1. Review backlog items in `_sprints/backlog/`
2. Move selected epics to a new sprint folder
3. Define stories within each epic
4. Ask Claude to create Jira tickets

### How do I prepare for a demo?
Create a demo summary in `_sprints/sprint-XX/demos/`. This gets synced to Confluence for stakeholders.

## Troubleshooting

### Claude isn't following our conventions
Check that the skills are properly referenced in `CLAUDE.md` and the skill files have correct content.

### Sync is failing
Run `/sync-confluence status` to check configuration. See the troubleshooting guide for common issues.

### Getting rate limited
Atlassian limits to ~120 requests/minute. Wait a few minutes and try again with smaller batches.
