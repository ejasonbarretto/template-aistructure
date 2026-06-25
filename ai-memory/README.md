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

**At the start of a session**, read (or have the assistant read):
1. `instructions/instructions.md`
2. `grounding/grounding.md`
3. `guardrails/guardrails.md`
4. The most recent file in `sessions/`

**At the end of a session**, run `/save-session` to log what happened. If the session produced a
durable decision (a new convention, a new piece of domain knowledge, a new constraint), update
`instructions/`, `grounding/`, or `guardrails/` directly — don't leave it stranded only in the
session log.
