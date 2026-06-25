# sessions/

A log of past AI-assisted working sessions, one file per session, written via `/save-session`.

## Naming convention

`YYYY-MM-DD-topic.md` — date the session happened, plus a short kebab-case topic slug. If there's
more than one session on the same topic in a day, append `-2`, `-3`, etc.

## Format

Each session log uses this structure:

```markdown
# Session: YYYY-MM-DD — Topic

## Objective
What the user asked for / the goal of this session.

## What we did
Concrete actions taken, files created/changed, decisions implemented.

## Decisions & rationale
Notable choices made and why (especially anything non-obvious or that overrides a default).

## Open items / next steps
Unfinished work, follow-ups, or things to revisit next session.
```
