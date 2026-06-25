---
name: save-session
description: Save a structured log of the current AI-assisted work session into ai-memory/sessions/. Use when the user asks to save, log, record, or wrap up the session, or wants this conversation's work persisted for next time.
---

# Save Session

Write a session log capturing what happened in this conversation so future sessions (with this
assistant or any other) can pick up context quickly.

## Steps

1. Determine today's date (`YYYY-MM-DD`) and a short kebab-case slug summarizing the session
   topic. If a file with that name already exists in `ai-memory/sessions/`, append `-2`, `-3`, etc.
2. Create `ai-memory/sessions/YYYY-MM-DD-topic.md` using the template below.
3. Fill in each section from the actual conversation — do not invent details. If a section has
   nothing relevant, write "None" rather than omitting it.
4. If this session produced a durable decision (a new working convention, a piece of domain
   knowledge, or a constraint), update `ai-memory/instructions/instructions.md`,
   `ai-memory/grounding/grounding.md`, or `ai-memory/guardrails/guardrails.md` directly — don't
   leave it stranded only in the session log.
5. Tell the user the path of the file you wrote.

## Template

```markdown
# Session: {{date}} — {{topic}}

## Objective
What the user asked for / the goal of this session.

## What we did
Concrete actions taken, files created/changed, decisions implemented.

## Decisions & rationale
Notable choices made and why (especially anything non-obvious or that overrides a default).

## Open items / next steps
Unfinished work, follow-ups, or things to revisit next session.
```
