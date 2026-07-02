# Session: 2026-07-02 — README adoption prompts

## Objective

Add copy-paste prompts to the root `README.md` so the user can bootstrap use of this template
in a new session just by pasting a filled-in prompt, for both a brand-new project and an
existing project being retrofitted with the `ai-memory/` workflow.

## What we did

- Replaced the "Starting a new project from this template" section in `README.md` with a new
  `## Adopting this template` section containing two scenarios, each ending in a fenced,
  ready-to-paste prompt:
  - **New project** — points the assistant at the template repo URL, asks for a project
    description and stack, and instructs it to adapt `project/` and fill in the three
    `ai-memory` content files.
  - **Existing project** — instructs the assistant to copy over only `.claude/skills/` and the
    `ai-memory/` folder structure (not `project/`), write the three content files from scratch
    rather than copying placeholders, and sanity-check the `workspace/<name>` branch workflow
    against the existing repo's git/CI setup.
- Both prompts reference the real repo URL and the actual skill/folder names already used in
  this template, so they stay accurate if pasted verbatim.

## Decisions & rationale

- **Two scenarios, not three** — user confirmed via AskUserQuestion that "new project" +
  "existing project" cover it; a third "joining a project that already uses this template"
  scenario was considered but not needed (that case is just `/start-session`, already
  documented elsewhere).
- **Replaced the old section rather than appending** — the old "Starting a new project" section
  only covered the new-project case as a plain list; folding it into the new prompt-based
  section avoids duplicating overlapping guidance.
- This closes the "template adoption guidance" open item flagged in the previous two sessions
  (`2026-07-02-improve-session-workflow.md` and `2026-07-02-workspace-branch-and-content-alignment.md`).

## Open items / next steps

- The other half of that older open item is still outstanding: add a visible
  `<!-- Schema only — write project-specific content here, do not copy from template -->`
  comment at the top of `ai-memory/instructions/instructions.md`, `grounding/grounding.md`, and
  `guardrails/guardrails.md`, so it's obvious those three files must be rewritten (not copied)
  when adopting the template.
- Consider adding a `/checkpoint` skill for intermediate commits during long sessions (carried
  over from earlier sessions, still unaddressed).
