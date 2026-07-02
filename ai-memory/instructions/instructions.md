# Instructions

How we work together on this project. Fill this in as conventions get established — keep it
current rather than letting it go stale.

## Tools & stack

_e.g. Python 3.12, dbt, Airflow, Snowflake — whatever this project actually uses._

## Git & GitHub

Remote: `https://github.com/ejasonbarretto/template-aistructure.git`. Push access requires the
`ejasonbarretto` GitHub account — `jason-engineer01` (also authenticated via `gh` on this machine)
does not have access and will get a 403. Check `gh auth status`; switch with
`gh auth switch --hostname github.com --user ejasonbarretto` if needed.

**Developer branch**: `workspace/jason`
_(Update this value when adopting this template in a new project — `/start-session` and
`/save-session` read it from here.)_

**Branching convention**:
- All session work happens on the developer's persistent `workspace/<name>` branch.
- Never commit directly to `main`.
- At the end of each session, `/save-session` pushes `workspace/<name>`, opens a PR to `main`,
  and auto-merges it — keeping `main` always current after every session.
- The workspace branch is **never deleted**; it persists across sessions.

## Coding conventions

_e.g. formatting/linting tools, naming conventions, testing expectations._

## Communication preferences

_e.g. how verbose responses should be, when to ask vs. assume, how changes should be reviewed
before being applied._

## Workflow

_e.g. branching strategy, how PRs are reviewed, how work gets deployed._
