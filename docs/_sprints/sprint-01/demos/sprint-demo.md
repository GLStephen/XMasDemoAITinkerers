# Sprint 1 Demo

**Date:** December 6, 2024
**Duration:** 30 minutes
**Audience:** Stakeholders, Development Team

## Demo Objectives

Show the foundation capabilities established in Sprint 1:
1. Atlassian API connectivity
2. Confluence documentation sync
3. Project structure and workflows

## Demo Script

### Part 1: Project Overview (5 min)

**Show:**
- Repository structure
- CLAUDE.md and skill configuration
- Documentation folders

**Key Points:**
- "This is how we organize our project"
- "Claude has context through skills and CLAUDE.md"
- "Documentation lives in version control"

### Part 2: Confluence Sync (15 min)

**Demo Steps:**
1. Show a markdown file in `_sync/_confluence/`
2. Run `/sync-confluence status`
3. Make a small change to the file
4. Run `/sync-confluence sync`
5. Show the updated Confluence page

**Key Points:**
- "Single source of truth in git"
- "Automatic sync to Confluence"
- "Hierarchy maintained through folder structure"

### Part 3: API Integration (5 min)

**Demo Steps:**
1. Ask Claude to search Jira for recent issues
2. Show the MCP tool being called
3. Display the results

**Key Points:**
- "Claude can interact with our tools"
- "Real-time access to project data"

### Part 4: Q&A (5 min)

Anticipated questions:
- "How do we handle conflicts?" → Local is source of truth
- "Can non-developers use this?" → Yes, just edit markdown
- "What's next?" → Jira ticket creation in Sprint 2

## Success Criteria

- [ ] Confluence sync completes without errors
- [ ] Page hierarchy visible in Confluence
- [ ] API query returns results
- [ ] Stakeholders understand the value proposition

## Post-Demo Actions

- Share recording with absent stakeholders
- Collect feedback in `_inbox/feedback/`
- Update FAQ based on questions asked
