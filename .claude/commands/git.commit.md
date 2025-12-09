---
description: Commit changes to current branch
argument-hint: [topic or file-path] (optional)
tags: [cicd, git, commit, release]
---

# Commit Changes

Use the Task tool with `subagent_type: release-manager` to commit changes.

**Scope:**

- If `$ARGUMENTS` provided: Commit only files matching topic/path in `$ARGUMENTS`
- If no arguments: Commit only files modified during this Claude Code conversation session (files touched via Edit/Write/NotebookEdit tools in this conversation)

**Commit strategy preference:**

- **Prefer:** Feature commits (group related changes into one commit)
- **Fallback:** Atomic commits (only when changes are completely independent)

**Reporting requirement:**

After release-manager completes, reformat output following `/docs/technical/git-conventions.md:165-191`:

```
✅ PUSHED to origin/[branch]
- Commit: [hash]
- Files: [count] ([list])
- Impact: Remote repository updated
```

Or if not pushed:

```
✅ COMMITTED (not pushed)
- Commit: [hash]
- Files: [count] ([list])
- Branch: [branch]
```

Follow phase-specific workflow and conventions from `/docs/technical/git-conventions.md`.
