---
description: Create pull request for current branch
tags: [cicd, git, pr, release]
---

# Create Pull Request

**Phase requirements** (from `CLAUDE.md`):

- **Discovery/POC:** Not required (direct commits faster for iteration)
- **MVP:** Required for merging to main
- **Production:** Required + enhanced template (rollback plan, deployment notes)

Use the Task tool with `subagent_type: release-manager`

**Prompt**: "Execute Workflow B (Create Pull Request). Detect phase from CLAUDE.md, analyze current branch and all commits since divergence, draft phase-appropriate PR summary (MVP or Production template), push branch if needed, create PR with gh pr create, and report PR URL."

See PR templates in `docs/technical/git-conventions.md`
