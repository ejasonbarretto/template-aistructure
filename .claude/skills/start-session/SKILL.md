---
name: start-session
description: Start a new AI-assisted working session. Verifies the active GitHub and Claude accounts, checks out the developer's persistent workspace branch (synced with main), and loads context from ai-memory/ so the assistant is ready to work. Run this at the beginning of every session.
---

# Start Session

Run these steps in order before doing any project work.

## Steps

### 1. Verify GitHub account

Run `gh auth status` and show the output to the user. Then read
`ai-memory/instructions/instructions.md` to find the expected GitHub account for this repo and
call it out explicitly:

> Active GitHub account: **<active account from gh auth status>**
> Expected for this repo: **<account from instructions.md>**
> Match: ✓ / ✗

If they don't match, stop and tell the user to run:
```
gh auth switch --hostname github.com --user <expected-account>
```
Do not proceed until the accounts match.

### 2. Verify Claude account

Print the following prompt — this is a manual checkpoint since there is no CLI command to
reliably surface the active Claude Code login from inside a skill:

> **Claude account check**: please confirm you are logged in to Claude Code as the expected
> account. You can verify in Claude Code → Settings → Account.
>
> Expected: _(read from `ai-memory/instructions/instructions.md` if documented, otherwise ask
> the user to fill it in)_

Wait for the user to confirm before continuing.

### 3. Get the session topic

Ask the user: "What's the topic for this session? (short kebab-case slug, e.g.
`add-ingestion-pipeline`)"

This slug is used only for the session log filename — not for the branch name.

### 4. Check out the workspace branch

Read the developer's workspace branch name from `ai-memory/instructions/instructions.md`
(documented as `Developer branch: workspace/<name>`).

**If the branch does not exist yet** (first time setup):
```
git checkout main
git pull origin main
git checkout -b workspace/<name>
git push -u origin workspace/<name>
```

**If the branch already exists**, check it out and sync with main so any changes that landed
in main since the last session are included:
```
git checkout workspace/<name>
git pull origin workspace/<name>   # get any remote changes
git merge main                     # bring in latest from main
```

Confirm which branch is now active:
> Workspace branch: **workspace/<name>** ✓
> Synced with main — ready for new work.

### 5. Load and summarize context

Read these four files:
1. `ai-memory/instructions/instructions.md`
2. `ai-memory/grounding/grounding.md`
3. `ai-memory/guardrails/guardrails.md`
4. The most recently dated file in `ai-memory/sessions/`

Then give the user a brief summary (3–5 bullet points) of what's carried over from the last
session — decisions made, open items, anything to keep in mind. Don't just list the file
contents; synthesize the relevant context for today's work.

---

Session is now open. Confirm readiness to the user and wait for their first task.
