# 002 - Git Workflow Rules

## Branch

```text
development/document-git-workflow-rules
```

## Purpose

Document the repository workflow for this Chatwoot fork so future AI/Codex sessions can work consistently.

## Repository Identity

This Chatwoot codebase is a fork.

```text
origin   git@github.com:SaidurIUT/chatwoot.git
upstream https://github.com/chatwoot/chatwoot.git
```

`origin` is the fork where custom Brain Assistant work is pushed.

`upstream` is the official Chatwoot repo used only for pulling official updates.

## Branch Rules

- `custom_main` is the default stable branch.
- Do not work directly on `custom_main`.
- Start every change from the latest `custom_main`.
- Use focused branches such as:
  - `development/<short-purpose>`
  - `feat/<short-purpose>`
  - `bugfix/<short-purpose>`
  - `docs/<short-purpose>`

## Documentation Rule

Every meaningful change must have a sequenced document in:

```text
docs/custom-changes/
```

Naming format:

```text
001-local-docker-mailhog-signup.md
002-git-workflow-rules.md
003-next-change.md
```

Each document should include:

- Branch name.
- Purpose.
- Files changed.
- What changed.
- Why it changed.
- Verification steps.
- Git workflow used.

## Standard Workflow

Create a branch:

```sh
git switch custom_main
git pull origin custom_main
git switch -c development/<short-purpose>
```

Commit:

```sh
git status
git diff --check
git add <files>
git diff --check --cached
git commit -m "Clear commit message"
```

Push:

```sh
git push -u origin development/<short-purpose>
```

Merge into `custom_main`:

```sh
git switch custom_main
git pull origin custom_main
git merge --ff-only development/<short-purpose>
git push origin custom_main
```

## Updating From Official Chatwoot

```sh
git switch custom_main
git fetch upstream
git merge upstream/develop
git push origin custom_main
```

Then update active branches:

```sh
git switch development/<short-purpose>
git merge custom_main
```

## Verification

This document is complete when:

- Root `README.md` points future AI/Codex contexts to the workflow rules.
- Root `AI_CONTEXT_AND_GIT_RULES.md` exists.
- This sequenced Chatwoot change document exists.
