# Sprint Planning

This folder contains sprint planning artifacts that integrate with the Jira skill.

## Structure

```
_sprints/
├── sprint-01/           # Completed sprint
│   ├── README.md        # Sprint overview
│   ├── epic-*.md        # Epic specifications
│   └── demos/           # Demo summaries
├── sprint-02/           # Current sprint
│   ├── README.md
│   ├── epic-*.md
│   └── demos/
└── backlog/             # Future work
    ├── README.md
    └── epic-*.md
```

## Workflow

### 1. Define Epics
Create epic files using this structure:

```markdown
# Epic: [Name]

**Category**: [Feature/Enhancement/Tech Debt]
**Number**: [Sequential]
**Due Date**: YYYY-MM-DD

## Description
[What and why]

## Stories

### Story X.1: [Name]
**Points**: [1-8]

[Description]

#### Acceptance Criteria
- Criterion 1
- Criterion 2
```

### 2. Create Jira Tickets
Ask Claude: "Create Jira tickets from this epic"

Claude will:
- Create the epic with proper naming
- Create stories linked to the epic
- Set story points and custom fields

### 3. Track Progress
Update epic files as work progresses. Story status is tracked in Jira.

### 4. Prepare Demo
Before sprint end, create a demo summary in `demos/` folder.

## Sprint Schedule

| Sprint | Dates | Status |
|--------|-------|--------|
| Sprint 1 | Nov 25 - Dec 6 | Complete |
| Sprint 2 | Dec 9 - Dec 20 | Active |
| Sprint 3 | Jan 6 - Jan 17 | Planned |

## Backlog Management

Epics not yet scheduled live in `backlog/`. During sprint planning, move selected epics to the new sprint folder.
