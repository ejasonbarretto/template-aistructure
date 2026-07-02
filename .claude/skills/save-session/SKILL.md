---
name: save-session
description: Save a structured log of the current AI-assisted work session, then commit, push, and open a PR to main. Use when the user asks to save, log, record, or wrap up the session, or wants this conversation's work persisted for next time.
---

# Save Session

Close out the session by writing a log, committing all work to the session branch, and opening a
PR to `main` for review.

## Steps

### 1. Write the session log

Determine today's date (`YYYY-MM-DD`) and a short kebab-case slug summarizing the session topic.
If a file with that name already exists in `ai-memory/sessions/`, append `-2`, `-3`, etc.

Create `ai-memory/sessions/YYYY-MM-DD-topic.md` using the template below. Fill in each section
from the actual conversation — do not invent details. If a section has nothing relevant, write
"None" rather than omitting it.

### 2. Update durable context files

If this session produced a durable decision (a new working convention, a piece of domain
knowledge, or a constraint), update the relevant file directly — don't leave it stranded only in
the session log:
- `ai-memory/instructions/instructions.md` — working conventions, tools, preferences
- `ai-memory/grounding/grounding.md` — domain knowledge, schemas, glossary
- `ai-memory/guardrails/guardrails.md` — hard constraints, things never to do

### 3. Check the session branch

Run `git branch --show-current` to confirm you are on a `session/` branch. If the current branch
is `main`, **stop** and warn the user:

> ⚠️ You are on `main`. Work should not be committed directly to `main`.
> Run `/start-session` first to create a session branch, or manually run:
> `git checkout -b session/YYYY-MM-DD-<topic>`

Do not proceed with the commit until on a session branch.

### 4. Commit all changes

```
git add -A
git commit -m "Session: YYYY-MM-DD — <topic>"
```

### 5. Push the session branch

```
git push -u origin session/YYYY-MM-DD-<topic>
```

### 6. Open a PR to main

Using the session log's **Objective** and **What we did** sections as the body:

```
gh pr create \
  --title "Session: YYYY-MM-DD — <topic>" \
  --body "## Objective\n<from session log>\n\n## What we did\n<from session log>" \
  --base main
```

### 7. Report to the user

Print the PR URL and confirm the session is fully saved.

---

## Session log template

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
