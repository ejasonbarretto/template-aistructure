# Session: 2026-07-02 — Workspace branch and content alignment

## Objective

Two goals in this session:
1. Replace the ephemeral `session/YYYY-MM-DD-topic` branching model with a persistent
   `workspace/<name>` branch per developer, and auto-merge to `main` at session end so `main`
   always stays current.
2. Fill in the three ai-memory content files (`instructions`, `grounding`, `guardrails`) with
   the real conventions, context, and constraints established across the bootstrap sessions —
   removing all placeholder text.

## What we did

- Rewrote `.claude/skills/start-session/SKILL.md` — step 4 now checks out `workspace/jason`
  (creating it from `main` if first time), then syncs it with `git merge main` before starting work.
- Rewrote `.claude/skills/save-session/SKILL.md` — after committing and pushing `workspace/jason`,
  it now opens a PR to `main` and immediately auto-merges with `gh pr merge --merge` (no manual
  merge step, workspace branch is never deleted).
- Updated `ai-memory/instructions/instructions.md` — added `Developer branch: workspace/jason`
  field and updated the branching convention to reflect the new model.
- Updated `ai-memory/README.md` — step 1 now describes checking out/syncing `workspace/<name>`,
  and step 3 describes auto-merge rather than leaving PR open.
- Populated `ai-memory/instructions/instructions.md` with real content: tools (Claude Code,
  gh, git on Windows 11), Git/GitHub account rules, coding conventions (SKILL.md format, session
  naming), communication preferences (plan-first, concise, manual approval), and the session workflow.
- Populated `ai-memory/grounding/grounding.md` with real content: what the template is and why it
  exists, the ai-memory folder as the project's "schema", a glossary of key terms, and stakeholders.
- Populated `ai-memory/guardrails/guardrails.md` with real rules: no data/credentials, never
  commit to `main` directly (fixing stale `session/` branch reference), never break skill files
  without thinking through the full flow, never skip plan mode, what requires prior approval.

## Decisions & rationale

- **Persistent workspace branch over per-session branches** — `session/YYYY-MM-DD-topic` branches
  left `main` perpetually stale (PR sat open, never auto-merged). `workspace/<name>` is persistent,
  represents the developer's identity, and is the natural target for end-of-session merges.
- **Auto-merge with `gh pr merge --merge`** — creates a standard merge commit so each session is
  visible as a distinct unit in `main`'s history. `--delete-branch` is intentionally omitted since
  the workspace branch persists.
- **Content files written from scratch, not copied from template** — confirmed: when adopting this
  template in a new project, only `.claude/skills/` and the ai-memory folder structure should be
  copied; the three content files must be rewritten for that project's specific context.

## Open items / next steps

- `workspace/jason` branch does not yet exist — needs to be created from `main` as the first act
  after this session's changes merge. This is the bootstrapping gap: we defined the convention
  during the same session we were building it, so we couldn't use it for this session itself.
- The template's content files (instructions, grounding, guardrails) should include a visible
  `<!-- Schema only — rewrite for your project, do not copy content -->` comment at the top, plus
  adoption guidance in the root `README.md` (carried over from previous session open item).
- Consider adding a `/checkpoint` skill for intermediate commits during long sessions.
