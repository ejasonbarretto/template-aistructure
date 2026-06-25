# Session: 2026-06-25 — Template bootstrap

## Objective

Design and create a reusable template repo for Data Engineering tasks done with an AI assistant.
The template needed two clearly separated parts: a place where the actual project work happens,
and a place where the AI assistant's durable context and session history lives.

## What we did

- Initialized this empty folder as a git repository (`main` branch) and added
  `origin` → `https://github.com/ejasonbarretto/template-aistructure.git` (verified empty before
  connecting).
- Created `project/` as a generic, stack-agnostic scaffold: `src/`, `sql/`, `notebooks/`,
  `tests/`, `data/` (gitignored contents), each with a short README.
- Created `ai-memory/` with four subfolders:
  - `instructions/instructions.md` — fill-in template for working conventions
  - `grounding/grounding.md` — fill-in template for domain/business context
  - `guardrails/guardrails.md` — fill-in template for hard constraints
  - `sessions/` — this log, plus a README documenting the naming convention and template
- Created the `/save-session` Claude Code skill
  (`.claude/skills/save-session/SKILL.md`) that writes a new structured log into
  `ai-memory/sessions/` on request.
- Wrote the root `README.md` explaining the template's purpose, structure, and session workflow.
- Wrote `.gitignore` covering Python/notebook/OS/editor noise plus `project/data/*`.

## Decisions & rationale

- **AI memory is plain in-repo markdown**, not Claude Code's native `~/.claude` memory system —
  chosen so the context is portable across AI tools and machines, and lives in git history with
  the rest of the project rather than in a tool-specific, machine-local location.
- **Session logging is manual** (`/save-session`, run on request) rather than an automatic
  Stop-hook — keeps the log curated and avoids capturing noise from every session regardless of
  whether anything worth recording happened.
- **No CLAUDE.md auto-load layer** was added on top of `ai-memory/` — this was a deliberate choice
  to keep the memory mechanism tool-agnostic rather than wiring it specifically into Claude Code's
  session-start behavior. (If auto-loading into Claude Code specifically is wanted later, add a
  `CLAUDE.md` that points at `ai-memory/instructions/`, `grounding/`, and `guardrails/`.)
- **`project/` scaffold is generic/stack-agnostic** rather than pinned to a specific DE stack
  (e.g. dbt, Airflow), since this template will be reused across projects with different stacks.

## Open items / next steps

- No `CLAUDE.md` auto-load wiring exists yet — revisit if Claude-Code-specific auto-context-load
  turns out to be wanted after all.
- `instructions.md`, `grounding.md`, and `guardrails.md` are still fill-in templates with no
  project-specific content — populate them once a real DE project starts using this template.
- Initial commit and push to `origin main` still need to happen after this log is written.
