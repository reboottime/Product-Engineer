# Commit Changes

Commits follow **phase-specific workflow** (detected from `CLAUDE.md`):

- **Discovery:** Docs preferred, auto-push to main, code triggers warning
- **POC:** Direct to main, auto-push (no permission needed)
- **MVP:** Branches required, PRs required, never push to main directly
- **Production:** Branches required, PRs required, never push to main directly (no exceptions)

Use the Task tool with `subagent_type: release-manager`

**Prompt**: "Execute commit workflow: Detect phase from CLAUDE.md, detect current branch, run pre-flight checks, analyze staged/unstaged changes for atomic commits (following git-conventions.md line 92), create separate commits for each logical change with message incorporating: $ARGUMENTS, apply phase-specific push strategy per git-conventions.md (auto-push for Discovery/POC/feature-branches, commit-only for MVP/Production on main with PR reminder), and report results."

**Critical:** Enforce atomic commits - split unrelated changes into separate commits following `docs/technical/git-conventions.md`
