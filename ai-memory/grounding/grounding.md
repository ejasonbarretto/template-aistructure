# Grounding

Domain and business context for this project.

## Business context

This is a **reusable template repo** for AI-assisted Data Engineering work. It is not a data
project itself — it is the scaffolding that gets cloned/forked as the starting point for every
new DE project.

The template solves a recurring problem: without a standard structure, AI assistants on DE
projects start each session with no context, work accumulates with no history, and conventions
drift across projects. This template provides:

- A consistent folder structure (`project/` for work, `ai-memory/` for context)
- Session bookend skills (`/start-session`, `/save-session`) that load context and persist it
- A branching convention (`workspace/<name>` → auto-merge PR → `main`) that keeps history clean

**Who uses it**: Jason, as the starting point for DE projects. When a new DE project begins,
this repo is cloned and the ai-memory content files are rewritten for that project's domain.

## Data sources & schemas

Not applicable — this is a template, not a data project. There are no data sources or schemas.

The closest equivalent is the **ai-memory folder structure itself**, which is the "schema" for
how context is organized across sessions:

| File | Contains |
|---|---|
| `ai-memory/instructions/instructions.md` | How we work, tools, conventions, workflow |
| `ai-memory/grounding/grounding.md` | Domain context (this file) |
| `ai-memory/guardrails/guardrails.md` | Hard constraints |
| `ai-memory/sessions/YYYY-MM-DD-topic.md` | Per-session logs |

## Glossary

| Term | Meaning |
|---|---|
| **ai-memory** | The folder in each project repo that holds all AI durable context as plain markdown |
| **session log** | A markdown file in `ai-memory/sessions/` capturing what happened in one working session |
| **workspace branch** | The persistent per-developer git branch (`workspace/<name>`) where all session work happens |
| **skill** | A Claude Code `.claude/skills/<name>/SKILL.md` file that defines a reusable, invokable action |
| **grounding** | Domain/business context the assistant needs to make good decisions |
| **guardrails** | Hard constraints the assistant must never violate |
| **durable context** | Information in `instructions/`, `grounding/`, or `guardrails/` that persists across sessions (as opposed to session logs, which are point-in-time) |

## Stakeholders

| Who | Role |
|---|---|
| Jason (`ejasonbarretto`) | Sole developer and maintainer of this template |
