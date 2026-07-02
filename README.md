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

## Adopting this template

Copy the prompt for your scenario, fill in the `<...>` placeholders, and paste it into a new
assistant session to bootstrap the setup automatically.

### New project

1. Create a new repo from this template (or clone it and re-point the remote).
2. Paste this prompt:

   ```
   Use this repo as the project folder structure and AI-assisted workflow template:
   https://github.com/ejasonbarretto/template-aistructure.git

   This is a new project. <describe what the project does, its goals, and stakeholders>
   Tech stack: <e.g. dbt, Airflow, Spark, Snowflake, Python — or "not decided yet, help me choose">

   Please:
   1. Adapt the project/ subfolders to this stack (rename/add/remove folders as needed).
   2. Fill in ai-memory/instructions/instructions.md, ai-memory/grounding/grounding.md, and
      ai-memory/guardrails/guardrails.md with the specifics of this project — ask me questions
      where you need more context.
   3. Run /save-session to log this bootstrap session once set up.
   ```

### Existing project

Use this when you want the `ai-memory/` workflow in a project that already has its own code and
structure. This intentionally leaves `project/` out and does not copy the content files verbatim
— they need to reflect the real project, not the template's placeholders.

1. In your existing repo, paste this prompt:

   ```
   Use this repo's ai-memory/ structure and session workflow as a template for AI-assisted work
   in this existing project: https://github.com/ejasonbarretto/template-aistructure.git

   This is an existing codebase — <briefly describe what it does>. Do NOT restructure or move
   any of my existing code.

   Please:
   1. Copy over only the .claude/skills/ folder and the ai-memory/ folder structure
      (instructions/, grounding/, guardrails/, sessions/ with their README.md files) — leave
      project/ out entirely, since this project already has its own layout.
   2. Write ai-memory/instructions/instructions.md, ai-memory/grounding/grounding.md, and
      ai-memory/guardrails/guardrails.md from scratch based on this project's real conventions,
      domain, and constraints — do not copy the template's placeholder content. Ask me questions
      where you need context.
   3. Confirm the workspace/<name> branch + /start-session + /save-session workflow fits how
      this repo's git workflow already works, and flag anything that conflicts with existing
      branch protections or CI.
   ```

## Session workflow

- **Start of session**: read `ai-memory/instructions/`, `ai-memory/grounding/`,
  `ai-memory/guardrails/`, and the most recent file in `ai-memory/sessions/`.
- **Do the work** in `project/`.
- **End of session**: run `/save-session` to log what happened (see
  [.claude/skills/save-session/SKILL.md](.claude/skills/save-session/SKILL.md)).

See [ai-memory/README.md](ai-memory/README.md) for the full breakdown.
