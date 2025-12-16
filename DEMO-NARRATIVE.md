# AI as a Translation Layer Across Organizational Boundaries

**Duration:** 5 minutes
**Audience:** AI Tinkerers - hands-on builders who bridge tech and business

---

## The Problem (30 sec)

Translation work lives in people's heads:

- **How do we name tickets?** Ask Sarah - she knows the convention.
- **How do we summarize for business?** Rewrite it every time. Hope it's consistent.
- **Does this feedback conflict with our plans?** Nobody knows until it's too late.

This translation overhead exists in every organization. It's expensive, lossy, and doesn't scale.

---

## The Pattern (30 sec)

**AI as translation layer:**

```
Implicit knowledge    →    Explicit rules    →    AI applies them
(in people's heads)        (in markdown)          (consistently)
```

Three properties:
1. Rules are visible and editable
2. AI follows the rules, doesn't invent them
3. Humans review the output

---

## Live Demo (3 min)

### Show 1: The Inbox Analyzer (~2 min)

"Here's an inbox with feedback from three sources - stakeholders, developers, and UX."

**Run:**
```
/analyze-inbox docs/_inbox/feedback/
```

**Show the output** (`analyze-inbox.sample.md`):

| Category | Count |
|----------|-------|
| Agreements | 7 |
| **Conflicts** | **5** (need resolution) |
| New Concepts | 13 |
| Action Items | 12 |

"Five conflicts found automatically. Thirteen new concepts that aren't in our docs yet. Twelve action items extracted from meeting notes and feedback."

"This is organizational drift made visible."

---

### Show 2: The Translation Rules (~1 min)

**Flip through the files:**

`.claude/skills/jira.md`:
```markdown
## Naming Conventions
### Epics
Format: `[Category]: [Epic Name] - [Number]`
Example: `Feature: User Authentication - 1`
```

"These are our Jira conventions. They used to live in the tech lead's head."

`.claude/commands/analyze-inbox.md`:
```markdown
For each document found, identify:
- Agreements (Confirms Existing Docs)
- Conflicts (Contradicts Existing Docs)
- New Concepts (Not in Current Docs)
```

"This is the analysis prompt. It's just markdown with structure."

**Key point:** "The AI follows explicit rules we wrote. No magic."

---

## The Takeaway (1 min)

**"Shifting out"** = moving translation work from heads to artifacts

Three things you can build tonight:

| Build This | It Does This |
|------------|--------------|
| **Skills** | Encode conventions (dev → PM translation) |
| **Sync commands** | Push to business tools (technical → business translation) |
| **Analysis commands** | Detect drift (organizational memory) |

The pattern is tool-agnostic. Swap Jira for Linear. Swap Confluence for Notion. The rules live in markdown.

**The principle:**

> AI doesn't make decisions. It makes translation explicit and repeatable.

---

## Q&A Prep

| Question | Answer |
|----------|--------|
| "Can I use this with [other tool]?" | Yes - swap the MCP. The pattern stays the same. |
| "What about hallucination?" | AI follows explicit rules. Humans review output. |
| "How long did this take?" | Structure: ~1 hour. The insight: longer. |
| "What's the hard part?" | Getting the rules explicit. Once written, AI scales them. |

---

## Files to Show

| File | What It Demonstrates |
|------|---------------------|
| `docs/_inbox/feedback/` | Raw organizational input (multiple voices) |
| `analyze-inbox.sample.md` | Drift detection output |
| `.claude/skills/jira.md` | Conventions made explicit |
| `.claude/commands/analyze-inbox.md` | Analysis protocol |

---

## The One-Liner

If anyone asks what this is:

> "We built AI that makes translation across organizational boundaries explicit and repeatable - so knowledge survives when people leave the room."
