# Developer Suggestions

**Source:** Team Retro & Slack
**Date:** December 14, 2024
**Collected By:** Tech Lead

## Suggestions Received

### 1. Auto-complete for Jira Fields

**From:** Developer A
**Suggestion:** Claude should suggest valid values for select fields like "Account" instead of requiring IDs.

**Discussion:**
- Would require querying Jira for field options
- Could cache field metadata
- Improves UX significantly

**Action:** Add to Jira integration epic as enhancement

---

### 2. Dry Run Mode

**From:** Developer B
**Suggestion:** Add a way to preview what tickets would be created without actually creating them.

**Discussion:**
- Show what would be created
- Validate before commit
- Catch errors early

**Action:** Add as story to backlog

---

### 3. Sync Diff Preview

**From:** Developer A
**Suggestion:** Before Confluence sync, show what pages will be created/updated.

**Discussion:**
- Similar to git diff
- Helps catch mistakes
- Could be part of status command

**Action:** Enhance /sync-confluence status

---

### 4. Epic File Generator

**From:** Developer C
**Suggestion:** Generate epic file skeleton from Jira epic, not just the other way around.

**Discussion:**
- Useful for existing work
- Bidirectional sync
- More complex to implement

**Action:** Add to backlog for Q2

## Priority Assessment

| Suggestion | Value | Effort | Priority |
|------------|-------|--------|----------|
| Auto-complete | High | Medium | P2 |
| Dry run | High | Low | P1 |
| Sync diff | Medium | Low | P2 |
| Epic generator | Medium | High | P3 |

## Next Steps

1. Add dry run to Sprint 3
2. Review others during backlog grooming
