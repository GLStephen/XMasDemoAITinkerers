# Sprint 2 Demo

**Date:** December 20, 2024
**Duration:** 30 minutes
**Audience:** Stakeholders, Development Team

## Demo Objectives

Showcase Jira integration capabilities:
1. Automated epic creation from markdown
2. Story creation with proper linking
3. Custom field handling
4. End-to-end workflow

## Demo Script

### Part 1: Recap & Context (3 min)

**Show:**
- Sprint 1 deliverables (Confluence sync)
- Sprint 2 goals
- Current project structure

**Key Points:**
- "Building on our Confluence sync foundation"
- "Now tackling the other side - Jira integration"

### Part 2: Jira Skill Overview (5 min)

**Show:**
- `.claude/skills/jira.md` file
- Naming conventions
- Custom field mappings

**Key Points:**
- "Claude now knows our Jira conventions"
- "Consistency without memorization"
- "Configurable per project"

### Part 3: Epic Creation Demo (10 min)

**Demo Steps:**
1. Open an epic spec file (e.g., `epic-jira-integration.md`)
2. Highlight the structured format
3. Ask Claude: "Create a Jira epic from this spec"
4. Show the MCP tool call
5. Open Jira to show created epic

**Key Points:**
- "Markdown in, Jira tickets out"
- "Proper naming applied automatically"
- "Custom fields populated"

### Part 4: Story Creation Demo (7 min)

**Demo Steps:**
1. Point to stories in the epic spec
2. Ask Claude: "Create stories for this epic"
3. Show stories being created
4. Open Jira to show hierarchy

**Key Points:**
- "Stories linked to epic automatically"
- "Story points set from spec"
- "Acceptance criteria in description"

### Part 5: Q&A (5 min)

Anticipated questions:
- "Can we modify after creation?" → Yes, Jira remains source of truth for status
- "What about sprints?" → Manual assignment for now
- "Bulk updates?" → Future enhancement

## Success Criteria

- [ ] Epic created with correct naming
- [ ] Stories linked to epic
- [ ] Custom fields populated correctly
- [ ] Stakeholders see time savings value

## Demo Environment Prep

- [ ] Clean test project in Jira
- [ ] Fresh epic spec file
- [ ] MCP connection verified
- [ ] Backup demo script if live fails

## Post-Demo Actions

- Share recording
- Collect feedback
- Update roadmap based on input
- Plan Sprint 3
