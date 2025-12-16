# Inbox

Incoming items awaiting triage and processing.

## Purpose

The inbox is a landing zone for:
- Meeting notes
- Feature requests
- Feedback from stakeholders
- Ideas and suggestions
- External input

## Structure

```
_inbox/
├── meetings/     # Meeting notes and action items
├── requests/     # Feature requests and enhancements
└── feedback/     # Stakeholder and user feedback
```

## Triage Workflow

### Weekly Triage (Fridays)

1. **Review all new items** in inbox
2. **Categorize** each item:
   - Actionable → Move to `_sprints/backlog/` as epic/story
   - Documentation → Move to `_sync/_confluence/`
   - Reference only → Archive or delete
3. **Update tracking** - Mark items as processed

### Triage Questions

For each item, ask:
- Is this actionable? (Yes → Backlog)
- Does this need stakeholder visibility? (Yes → Confluence)
- Is this time-sensitive? (Yes → Current sprint)
- Is this a duplicate? (Yes → Merge/delete)

## Conventions

### Meeting Notes
- Filename: `YYYY-MM-DD-[topic].md`
- Include: attendees, decisions, action items
- Tag action items for follow-up

### Feature Requests
- Filename: `[short-name].md`
- Include: problem, proposed solution, value
- Note requester and date

### Feedback
- Filename: `[source]-feedback.md`
- Include: source, date, raw feedback
- Note any immediate actions needed

## Current Items

| Folder | Count | Oldest |
|--------|-------|--------|
| meetings/ | 3 | Dec 10 |
| requests/ | 3 | Dec 12 |
| feedback/ | 3 | Dec 14 |

**Last Triage:** December 13, 2024
