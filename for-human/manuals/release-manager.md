# Release Manager - Quick Reference

## Quick Start

**Agent invocation:**

```
@agent-release-manager [your instruction]
```

**Examples:**

- `commit and push`
- `create a PR`
- `commit but don't push`

**Slash commands:**

```
/git.commit    # Same as agent invocation
/git.add-pr    # Create PR
```

**Agent decides:** Feature commit (groups related) or atomic (separate independent changes)

**Use for:** Commits, pushes, PRs
**Won't do:** Code review, planning, complex git surgery

## What It Needs

- Your instruction ("commit and push", "create PR", etc.)
- Working directory with changes
- Current phase from `CLAUDE.md` (auto-detects)

## What You Get

**Success:**

```
✅ [abc1234] (discovery) docs(product): add user interview insights
✅ origin/main • 📝 3 files
```

**Blocked:**

```
❌ Cannot push to main in MVP phase
💡 git checkout -b feature/[name]
```

## Phase Rules

| Phase | Push to Main? | Feature Branches | PR Required |
|-------|---------------|------------------|-------------|
| **Discovery** | ✅ Docs only | ✅ Auto-push | ❌ |
| **POC** | ✅ Everything | ✅ Auto-push | ❌ |
| **MVP/Production** | ❌ PR only | ✅ Auto-push | ✅ |

## Safety Blocks

**Will refuse:**

- Secrets (.env, API keys, credentials)
- Push to main in MVP/Production
- Invalid branch names in MVP/Production
- Detached HEAD, merge conflicts, no changes

**Gives recovery commands when blocked.**

## Common Scenarios

| Scenario | Command | Result |
|----------|---------|--------|
| **Discovery: Docs** | `commit and push` | ✅ Pushes to main |
| **MVP: Feature branch** | `commit and push` | ✅ Pushes to origin/feature/x |
| **MVP: On main** | `commit and push` | ❌ Blocked, suggests feature branch |
| **Create PR** | `create a PR` | ✅ Analyzes commits, pushes, creates PR |

## Common Fixes

| Problem | Recovery |
|---------|----------|
| Committed, not pushed | `git push` |
| Wrong commit message | `git commit --amend -m "fix"` |
| Split commits | `git reset HEAD~1` |
| Pushed to main by mistake | `git revert [hash]` (never force push) |
| Hook changed files | Agent auto-amends if safe |

## Commit Format

```
type(scope): description
```

**Types:** `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`
**Scope:** Component affected (auth, api, ui, etc.)
**Groups related changes into one commit by default.**

## Branch Names (MVP/Production)

Must use: `feature/*`, `bugfix/*`, or `hotfix/*`

---

**That's it.** Agent handles the rest.
