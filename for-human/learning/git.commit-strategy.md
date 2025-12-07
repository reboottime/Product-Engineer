# Git Commit Strategy: Feature vs Atomic

## The Question

When should you group changes into one commit vs split into multiple commits?

## The Answer

**Default to feature commits** (group related changes together).

### Feature Commits (Use 95% of the time)

Group all changes for one logical feature/fix into **one commit**.

**Examples:**

- Adding dark mode → 1 commit (CSS + JS + config + tests)
- Fixing login bug → 1 commit (backend fix + frontend update + test)
- Updating dependencies → 1 commit (package.json + lock file + code adjustments)

**Why?**

- Clear story: "Added dark mode" vs 5 cryptic commits
- Easy to revert: Remove entire feature in one step
- Better reviews: One PR = one commit = one concept
- Real-world standard: Most professional teams work this way

### Atomic Commits (Use only when changes are unrelated)

Split into separate commits when you did **multiple independent things** in one session.

**Examples:**

- Fixed 3 unrelated bugs → 3 commits
- Updated docs + fixed security issue → 2 commits
- Refactored code + added new feature → 2 commits

**Why?**

- Different changes might need different review/approval
- Can cherry-pick or revert independently
- Clear git history shows distinct work

## Quick Decision Tree

```
Are the changes part of ONE feature/fix?
├─ Yes → Feature commit (group together)
└─ No → Atomic commits (split apart)

Would you revert these changes together?
├─ Yes → Feature commit
└─ No → Atomic commits
```

## Common Mistakes

❌ **Over-splitting**: Breaking dark mode into 5 commits (CSS, JS, config, tests, docs)

- Result: Hard to understand what was added
- Better: One "feat(ui): add dark mode" commit

❌ **Over-grouping**: Combining bug fix + new feature in one commit

- Result: Can't revert feature without losing bug fix
- Better: Two separate commits

## Your Project Context

**Current phase:** Customer Discovery (direct to main)

- Granular commits make sense now (no PRs for grouping)
- **Later phases** (MVP/Production): Switch to feature commits when using PRs

## Next Steps

1. When starting work, ask: "Am I working on one thing or multiple unrelated things?"
2. Group related → one commit
3. Split unrelated → multiple commits
4. When in doubt → group it (easier to split later than combine)
