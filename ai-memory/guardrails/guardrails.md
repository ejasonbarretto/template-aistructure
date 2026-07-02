# Guardrails

Constraints the assistant must respect on this project. Fill this in as soon as a real constraint
is known — these should be treated as hard rules, not suggestions.

## Data handling

_e.g. PII/compliance rules, what data can leave the local environment, retention rules._

## Things never to do

- **Never commit or push directly to `main`** — all session work must happen on a
  `session/YYYY-MM-DD-topic` branch and reach `main` only through a reviewed PR.
- _Never run destructive operations against production data._
- _Never commit credentials, secrets, or raw data files._

## Approval required before

_e.g. schema changes, production deploys, anything that touches shared infrastructure._
