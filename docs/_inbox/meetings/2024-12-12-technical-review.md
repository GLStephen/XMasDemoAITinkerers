# Technical Review Meeting

**Date:** December 12, 2024
**Attendees:** Tech Lead, 2 Developers
**Duration:** 45 minutes

## Agenda

1. MCP configuration review
2. Jira skill design
3. Custom field mapping
4. Error handling approach

## Discussion Notes

### MCP Configuration
- Using `mcp-atlassian-api` package
- Config stored in `.claude/mcp.json`
- Environment variables for credentials
- Working with both Jira and Confluence

### Jira Skill Design
- Skill file defines naming conventions
- Custom fields documented with IDs
- Example tool calls included
- Referenced in CLAUDE.md

### Custom Field Mapping

| Field | Jira ID | Notes |
|-------|---------|-------|
| Story Points | customfield_10025 | Number field |
| Account | customfield_10080 | Select field |
| Epic Link | parent.key | Standard field |

**Finding:** Custom field IDs are instance-specific. Need to document discovery process.

### Error Handling
- MCP returns errors as tool results
- Claude should interpret and suggest fixes
- Common errors documented in troubleshooting
- Rate limit handling: exponential backoff

## Technical Decisions

1. **Store custom field IDs in skill** - Easy to update per instance
2. **Use parent.key for epic linking** - Standard Jira approach
3. **Default story points to 1** - Override in spec if needed
4. **No bulk creation** - Sequential to avoid rate limits

## Code Review Notes

Reviewed: Initial Jira skill draft
- Good: Clear naming conventions
- Good: Example tool calls
- Improve: Add more error scenarios
- Improve: Document field discovery

## Action Items

- [ ] @Developer1: Add field discovery docs - Due Dec 13
- [ ] @Developer2: Test epic creation - Due Dec 13
- [ ] @TechLead: Review error handling - Due Dec 14

## Follow-up

Test results review - December 16, 2024
