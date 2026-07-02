# Instructions

How we work together on this project. Keep this current — update it when a convention changes
rather than letting it go stale.

## Tools & stack

This is a **template repo**, not a data project — the "stack" is the tooling used to build and
maintain the template itself:

- **Claude Code** (Claude Sonnet) — the AI assistant; runs in VS Code extension on Windows 11
- **Git + GitHub CLI (`gh`)** — version control and PR management
- **Shell**: PowerShell (primary) and Bash tool both available; use Bash syntax for POSIX scripts
- **OS**: Windows 11 Home, so paths use backslashes in Explorer but forward slashes in shell tools

## Git & GitHub

Remote: `https://github.com/ejasonbarretto/template-aistructure.git`

Push access requires the `ejasonbarretto` account — `jason-engineer01` (also on this machine)
does not have access and will 403. Check `gh auth status`; switch with:
```
gh auth switch --hostname github.com --user ejasonbarretto
```

**Developer branch**: `workspace/jason`
_(Update this when adopting this template in a new project — `/start-session` and `/save-session`
read it from here.)_

**Branching convention**:
- All session work happens on the persistent `workspace/jason` branch — never commit to `main`.
- `/start-session` checks out `workspace/jason` (creating from `main` if first time) and syncs it with `main`.
- `/save-session` commits, pushes `workspace/jason`, opens a PR to `main`, and auto-merges — `main` is always current after every session.
- The workspace branch is never deleted.

## Coding conventions

- All AI memory content is plain markdown — no special syntax, no frontmatter (except SKILL.md files).
- Skill files (`.claude/skills/<name>/SKILL.md`) use YAML frontmatter with `name` and `description` fields.
- Session log filenames: `YYYY-MM-DD-topic.md` in `ai-memory/sessions/`, kebab-case topic slug.
- No code comments unless the WHY is non-obvious. No trailing summaries in responses.
- Keep READMEs scannable — short sentences, tables over prose where possible.

## Communication preferences

- **Plan before implementing** for anything non-trivial — enter plan mode, explore, get approval, then execute.
- **Ask, don't assume** on ambiguous design decisions (branch naming, merge strategy, etc.).
- **Concise responses** — one clear sentence per update while working; no multi-paragraph narration.
- **Manual approval of edits** — the user reviews each tool call; don't batch and execute without confirmation.

## Workflow

Every session follows the bookend pattern:
1. `/start-session` — verifies accounts, checks out `workspace/jason`, loads context
2. Do the work — plan first for non-trivial tasks, implement with user approval
3. `/save-session` — writes session log, commits, pushes, auto-merges PR to `main`
