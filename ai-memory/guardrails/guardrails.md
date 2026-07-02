# Guardrails

Hard constraints the assistant must respect on this project. These are rules, not suggestions.

## Data handling

This is a template repo — there is no real data. However:

- Never commit any data files (`.csv`, `.parquet`, `.db`, `.json` data dumps, etc.) even as
  examples — `project/data/` is gitignored for this reason.
- Never commit credentials, API keys, secrets, or `.env` files.

## Things never to do

- **Never commit or push directly to `main`** — all session work must happen on `workspace/jason`
  and reach `main` only through an auto-merged PR via `/save-session`.
- **Never merge a PR to `main` manually mid-session** — let `/save-session` handle it at the
  proper end-of-session point.
- **Never modify a skill's SKILL.md without running through its full flow mentally first** — skills
  are the core of the template's value; a broken skill breaks the workflow for every project that
  adopts this template.
- **Never delete the `workspace/jason` branch** — it is persistent by design.
- **Never skip plan mode for non-trivial changes** — enter plan mode, get approval, then implement.

## Approval required before

- Any change to skill logic (`.claude/skills/*/SKILL.md`) — these are the template's core.
- Any change to the session workflow described in `ai-memory/README.md`.
- Any structural change to the `ai-memory/` folder layout — downstream projects depend on this
  structure being stable.
- Pushing to the GitHub remote — confirm the active `gh` account is `ejasonbarretto` first.
