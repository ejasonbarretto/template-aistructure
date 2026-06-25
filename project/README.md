# project/

This is where the actual Data Engineering work happens — the real code, queries, notebooks,
data, and tests for whatever project this template was cloned into.

The subfolders below are a generic, stack-agnostic starting point. Adapt them to the real stack
of the project (e.g. swap `sql/` for a `dbt/` project, add `dags/` for Airflow, add `pipelines/`
for a specific orchestrator). Don't feel obligated to keep a folder if the project doesn't need it.

| Folder | Purpose |
|---|---|
| [src/](src/) | Pipeline / ETL / application code |
| [sql/](sql/) | SQL models, queries, transformations |
| [notebooks/](notebooks/) | Exploratory analysis, scratch work |
| [tests/](tests/) | Tests for the code in `src/` and `sql/` |
| [data/](data/) | Local-only data files (gitignored — never commit data) |

See [../ai-memory/README.md](../ai-memory/README.md) for how the AI assistant's context and
session history is tracked alongside this work.
