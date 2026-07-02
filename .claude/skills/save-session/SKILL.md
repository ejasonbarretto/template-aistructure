---
name: save-session
description: Save a structured log of the current AI-assisted work session, commit and push to the workspace branch, then auto-merge to main so main stays current. Use when the user asks to save, log, record, or wrap up the session.
---

# Save Session

Close out the session by writing a log, committing all work to the workspace branch, and
auto-merging into `main` so it stays up to date.

## Steps

### 1. Write the session log

Determine today's date (`YYYY-MM-DD`) and the session topic slug (ask the user if unknown, or
re-use the slug from `/start-session`). If a file with that name already exists in
`ai-memory/sessions/`, append `-2`, `-3`, etc.

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

### 3. Verify the workspace branch

Run `git branch --show-current`. The current branch must be `workspace/<name>` (read from
`ai-memory/instructions/instructions.md`). If it is `main` or anything else, **stop** and warn:

> ⚠️ You are not on the workspace branch.
> Expected: **workspace/<name>**
> Current: **<current branch>**
> Run `/start-session` to check out the correct branch before saving.

Do not proceed with the commit until on the workspace branch.

### 4. Commit all changes

```
git add -A
git commit -m "Session: YYYY-MM-DD — <topic>"
```

### 5. Push the workspace branch

```
git push origin workspace/<name>
```

### 6. Open a PR and auto-merge to main

Open the PR using the session log's **Objective** and **What we did** as the body:
```
gh pr create \
  --title "Session: YYYY-MM-DD — <topic>" \
  --body "## Objective
<from session log>

## What we did
<from session log>" \
  --base main
```

Then immediately auto-merge it (do **not** delete the workspace branch — it is persistent):
```
gh pr merge --merge
```

### 7. Confirm main is updated

Run `git log origin/main --oneline -3` and show the output so the user can confirm the session
commit landed on `main`.

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
