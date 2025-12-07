# Commit Changes

Commits follow **phase-specific workflow** (detected from `CLAUDE.md`):

- **Discovery:** Docs preferred, code triggers warning
- **POC:** Direct to main, auto-push (no permission needed)
- **MVP:** Branches preferred, ask before pushing to main
- **Production:** Branches required, PRs required, never auto-push to main

Use the Task tool with `subagent_type: release-manager`

**Prompt**: "Execute Workflow A (Commit & Push). Detect phase from CLAUDE.md, run pre-flight checks, analyze staged/unstaged changes for atomic commits (following git-conventions.md line 92), create separate commits for each logical change with message incorporating: $ARGUMENTS, push following phase-specific strategy, and report results."

**Critical:** Enforce atomic commits - split unrelated changes into separate commits following `docs/technical/git-conventions.md`
