# Epic: Jira Integration

**Category**: Feature
**Number**: 3
**Due Date**: 2024-12-20
**Status**: In Progress

## Description

Enable automated creation of Jira tickets from markdown specifications. Teams can define epics and stories in structured markdown, then have Claude create properly formatted Jira tickets following project conventions.

## Stories

### Story 3.1: Create Jira Skill
**Points**: 3
**Status**: Complete

Define the Jira skill with project conventions.

#### Tasks
- Define naming conventions for epics/stories
- Document custom field mappings
- Create skill file structure
- Add to CLAUDE.md reference

#### Acceptance Criteria
- Skill file in .claude/skills/
- Referenced in CLAUDE.md
- Naming conventions documented
- Custom fields mapped

---

### Story 3.2: Implement Epic Creation
**Points**: 2
**Status**: Complete

Enable creation of Jira epics from markdown.

#### Tasks
- Parse epic specification from markdown
- Map to Jira createIssue call
- Handle required fields (duedate, account)
- Return created epic key

#### Acceptance Criteria
- Epic created with correct naming
- Due date set correctly
- Account field populated
- Epic key returned for linking

---

### Story 3.3: Implement Story Creation
**Points**: 2
**Status**: In Progress

Enable creation of stories linked to epics.

#### Tasks
- Parse story specifications
- Link to parent epic
- Set story points
- Handle acceptance criteria

#### Acceptance Criteria
- Stories created with correct naming
- Linked to parent epic
- Story points set (default 1)
- Description includes AC

---

### Story 3.4: End-to-End Workflow Test
**Points**: 2
**Status**: Not Started

Validate complete workflow from markdown to Jira.

#### Tasks
- Create test epic specification
- Run full creation workflow
- Validate all fields in Jira
- Document any issues

#### Acceptance Criteria
- Epic created successfully
- All stories linked correctly
- Custom fields populated
- No manual cleanup needed
