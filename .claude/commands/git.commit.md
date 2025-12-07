---
description: Commit changes to current branch
tags: [cicd, git, commit, release]
---

# Commit Changes

Use the Task tool with `subagent_type: release-manager` to commit changes.

**Commit strategy preference:**

- **Prefer:** Feature commits (group related changes into one commit)
- **Fallback:** Atomic commits (only when changes are completely independent)

Follow phase-specific workflow and conventions from `/docs/technical/git-conventions.md`.
