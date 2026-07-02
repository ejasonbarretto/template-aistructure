# ai-memory/

This is the AI assistant's durable context for this project — plain markdown, version-controlled
with the rest of the repo, and readable by any AI assistant (not tied to one tool or machine).

| Folder | Purpose | Updated |
|---|---|---|
| [instructions/](instructions/instructions.md) | How we work together: conventions, tools, communication preferences | Whenever a working preference changes |
| [grounding/](grounding/grounding.md) | Domain/business context: data sources, schemas, glossary, stakeholders | Whenever domain knowledge changes |
| [guardrails/](guardrails/guardrails.md) | Things to avoid, compliance/safety/approval rules | Whenever a constraint is established |
| [sessions/](sessions/README.md) | Log of past working sessions | At the end of every session, via `/save-session` |

## Session workflow

**1. Start** — run `/start-session`
- Verifies the active GitHub and Claude accounts match what this repo expects
- Checks out the persistent `workspace/<name>` branch (creates it from `main` if first time),
  then syncs it with `main` so any changes from previous sessions are included
- Reads and summarizes context from the four files below so the assistant is ready to work

**2. Work** — do the actual DE work in `project/`
- All commits during the session go to the session branch
- You can commit intermediate progress at any point; it won't touch `main`

**3. End** — run `/save-session`
- Writes the session log to `ai-memory/sessions/`
- Updates `instructions/`, `grounding/`, or `guardrails/` if the session produced durable decisions
- Commits all changes, pushes `workspace/<name>`, opens a PR to `main`, and auto-merges it —
  `main` is always current after every session ends
