# Glossary

## A

**AI Assistance**
Using Claude to help with development tasks like code generation, documentation, and project management.

## C

**Claude Code**
Anthropic's CLI tool for AI-assisted development. Provides skills, commands, and tool integrations.

**Confluence Sync**
The process of pushing local markdown documentation to Confluence pages automatically.

**Custom Field**
Jira fields specific to your organization (e.g., customfield_10025 for story points).

## E

**Epic**
A large body of work in Jira that can be broken down into stories. In this project, epics are defined in markdown files.

## J

**Jira Skill**
A Claude Code skill that teaches Claude how to create Jira tickets following project conventions.

## M

**MCP (Model Context Protocol)**
A standard for connecting AI assistants to external tools and data sources. Claude Code uses MCP to interact with Jira and Confluence.

**Milestone**
A significant checkpoint in the project timeline marking completion of related deliverables.

## S

**Skill**
A Claude Code feature that provides context and conventions to Claude. Skills are always available (vs. commands which are invoked).

**Sprint**
A time-boxed period (typically 2 weeks) for completing planned work. Each sprint has defined epics and a demo.

**Story**
A unit of work in Jira representing a feature or task. Stories belong to epics and have story points.

**Story Points**
A relative measure of effort/complexity used for estimation. Stored in customfield_10025.

**Sync Footer**
A hidden markdown comment that tracks Confluence page ID and last sync time:
`[//]: # (confluence-sync: pageId=XXX, lastSyncedAt=...)`

## T

**Ticket**
Generic term for any Jira issue (epic, story, task, bug, etc.).

## W

**Workflow**
A defined sequence of steps for accomplishing a task, often automated or AI-assisted.
