# template-aistructure

A reusable template for Data Engineering work done with an AI assistant. Use this repo as a
GitHub template ("Use this template" button) to start every new DE project with the same
structure: a place for the real work, and a place for the assistant's durable context.

## Structure

```
project/        the actual Data Engineering work — code, SQL, notebooks, data, tests
ai-memory/      the AI assistant's durable context — instructions, grounding, guardrails, sessions
```

- **[project/](project/README.md)** is a generic, stack-agnostic scaffold. Adapt it to whatever
  the real project's stack turns out to be (dbt, Airflow, Spark, a specific warehouse, etc.).
- **[ai-memory/](ai-memory/README.md)** is plain markdown, version-controlled with the rest of the
  repo, and portable across AI tools — it's not tied to one assistant or machine.

## Starting a new project from this template

1. Create a new repo from this template (or clone it and re-point the remote).
2. Fill in `ai-memory/instructions/instructions.md`, `ai-memory/grounding/grounding.md`, and
   `ai-memory/guardrails/guardrails.md` with the specifics of the new project.
3. Adapt the `project/` subfolders to the real stack.

## Session workflow

- **Start of session**: read `ai-memory/instructions/`, `ai-memory/grounding/`,
  `ai-memory/guardrails/`, and the most recent file in `ai-memory/sessions/`.
- **Do the work** in `project/`.
- **End of session**: run `/save-session` to log what happened (see
  [.claude/skills/save-session/SKILL.md](.claude/skills/save-session/SKILL.md)).

See [ai-memory/README.md](ai-memory/README.md) for the full breakdown.
