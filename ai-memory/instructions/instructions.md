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

**Branching convention**: all session work happens on a `session/YYYY-MM-DD-topic` branch (e.g.
`session/2026-07-02-improve-workflow`). Never commit directly to `main`. At the end of each
session, `/save-session` pushes the branch and opens a PR to `main` for manual review and merge.

## Coding conventions

_e.g. formatting/linting tools, naming conventions, testing expectations._

## Communication preferences

_e.g. how verbose responses should be, when to ask vs. assume, how changes should be reviewed
before being applied._

## Workflow

_e.g. branching strategy, how PRs are reviewed, how work gets deployed._
