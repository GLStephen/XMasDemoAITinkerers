---
name: analyze-inbox
description: Analyze inbox documents against current docs to find agreements, conflicts, and new concepts
---

# Inbox Document Analysis

Analyze documents at the specified path against the current project documentation to identify alignments, conflicts, and new information.

**Path to analyze:** $ARGUMENTS

If no path is provided, default to `docs/_inbox/`.

## Analysis Process

### Step 1: Discover Documents

1. Read all `.md` files in the specified path (recursively if it's a directory)
2. Read the current documentation structure:
   - `docs/architecture/` - Technical architecture
   - `docs/features/` - Feature specifications
   - `docs/guides/` - How-to documentation
   - `docs/_sync/_confluence/` - Business documentation
   - `docs/_sprints/` - Sprint planning and epics

### Step 2: Analyze Each Inbox Document

For each document found, identify:

**Document Type:**
- Meeting notes → Compare against decisions, action items, technical details
- Feature requests → Compare against roadmap, existing features, backlog
- Feedback → Compare against current capabilities, known issues
- Other → General comparison

### Step 3: Generate Comparison Report

For each inbox document, produce a structured analysis:

```markdown
## [Document Name]

### Agreements (Confirms Existing Docs)
- [What this document confirms or aligns with]
- Reference: [link to existing doc]

### Conflicts (Contradicts Existing Docs)
- [What this document says differently]
- Existing doc says: [quote/summary]
- This document says: [quote/summary]
- Reference: [link to existing doc]

### New Concepts (Not in Current Docs)
- [New information, decisions, or concepts]
- Suggested location: [where this should be documented]

### Action Items Mentioned
- [ ] [Any action items found in the document]
```

### Step 4: Summarize Findings

Provide an overall summary:

```markdown
## Summary

| Category | Count | Priority |
|----------|-------|----------|
| Agreements | X | - |
| Conflicts | X | High (need resolution) |
| New Concepts | X | Medium (need documentation) |
| Action Items | X | Varies |

## Recommended Updates

### High Priority (Conflicts to Resolve)
1. [Conflict description] → Update [doc path]

### Medium Priority (New Concepts to Document)
1. [New concept] → Add to [doc path]

### Low Priority (Confirmations)
- [Documents that just confirm existing info - may not need action]
```

### Step 5: Plan Next Steps

After presenting the analysis, offer to:

1. **Create update tasks** - Generate stories in `_sprints/backlog/` for documentation updates
2. **Draft updates** - Write proposed changes to existing docs
3. **Archive processed items** - Move analyzed inbox items to an archive folder
4. **Create Confluence summary** - Add findings to `_sync/_confluence/status/`

## Example Usage

```
/analyze-inbox docs/_inbox/meetings/
/analyze-inbox docs/_inbox/feedback/stakeholder-feedback.md
/analyze-inbox docs/_inbox/
```

## Output Format

Present findings conversationally but structured. Use tables for summaries, bullet points for details, and clear headers for navigation.

After analysis, ask: "Would you like me to help plan updates based on these findings?"
