---
description: Commit changes to current branch
argument-hint: [topic or file-path] (optional)
tags: [cicd, git, commit, release]
---

Use Task tool with `subagent_type: release-manager` to commit changes.

**Arguments:** `$ARGUMENTS`

**Scope:** If arguments provided, commit all files related to that topic/feature/concept. Otherwise commit files modified in this session.

Follow workflow from `/docs/technical/git-conventions.md`.
