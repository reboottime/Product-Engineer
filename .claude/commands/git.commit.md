# Commit Changes

Commits follow **phase-specific workflow** (detected from `CLAUDE.md`):

- **Discovery:** Docs preferred, code triggers warning
- **POC:** Direct to main, auto-push (no permission needed)
- **MVP:** Branches preferred, ask before pushing to main
- **Production:** Branches required, PRs required, never auto-push to main

Use the Task tool with `subagent_type: release-manager`

**Prompt**: "Execute Workflow A (Commit & Push). Detect phase from CLAUDE.md, run pre-flight checks, commit all changes with message: $ARGUMENTS, push following phase-specific strategy, and report results."

Follow conventions in `docs/technical/git-conventions.md`
