# Designing Files for AI Agent Efficiency

## The Misconception

"AI agents can skip irrelevant sections in a file, so keeping everything in one place is fine."

**This is wrong.**

## How Agents Actually Read Files

When an agent uses the Read tool:

1. **Entire file loads** into context
2. **All tokens processed** (every line costs tokens)
3. **Headings help comprehension, NOT efficiency**
4. **No skipping** - agents can't selectively load sections

## Real Example

**Scenario:** Agent needs to check commit message format rules

**Current setup:** `git-conventions.md` (2700 tokens)

- Lines 1-200: Conventions (what agent needs)
- Lines 201-250: PR templates (irrelevant right now)
- **Agent loads all 2700 tokens** even though it only needs 200 lines

**Optimized setup:**

- `git-conventions.md` (1800 tokens) - conventions only
- `templates/pr-mvp.md` (500 tokens) - separate file
- **Agent loads only 1800 tokens** for convention lookup

**Savings:** 900 tokens per read (33% reduction)

## The Token Math

**Why this matters:**

| Operation | Frequency | Current Cost | Optimized Cost | Savings |
|-----------|-----------|--------------|----------------|---------|
| Check commit rules | 10x/day | 27,000 tokens | 18,000 tokens | 9,000 tokens/day |
| Create PR | 1x/week | 2,700 tokens | 2,400 tokens | 300 tokens/week |

**Net result:** Massive savings on frequent operations, tiny cost on rare ones.

## The Design Principle

**Split files by usage pattern, not just by topic.**

### Bad: Split by topic

```
docs/
  git.md                    ← Everything git-related
  product.md                ← Everything product-related
```

Result: Agent loads everything when it needs one thing

### Good: Split by usage + purpose

```
docs/technical/
  git-conventions.md        ← Rules (read frequently)
  templates/
    pr-mvp.md              ← Artifacts (read when needed)
```

Result: Agent loads only what it needs

## When to Split Files

**Split when:**

- ✅ Different parts used in different contexts
- ✅ File > 2000 tokens
- ✅ Contains both "rules" and "templates/examples"
- ✅ Some sections rarely needed

**Keep together when:**

- ❌ Always used together
- ❌ File < 1000 tokens
- ❌ Splitting creates more confusion than clarity

## Common Patterns

### Pattern 1: Rules vs Templates

```
conventions.md     ← How to do it (rules, decisions)
templates/         ← What to generate (artifacts)
```

### Pattern 2: Reference vs Examples

```
api-spec.md        ← API contracts, rules
examples/          ← Sample requests/responses
```

### Pattern 3: Strategy vs Tactics

```
strategy.md        ← Why, principles, goals
implementation/    ← How, step-by-step guides
```

## The Clarity Bonus

Smaller files aren't just more efficient - they're clearer:

- **Focused purpose** = easier to understand
- **Less noise** = better signal
- **Faster scanning** = quicker decisions
- **Lower cognitive load** = better comprehension

## Anti-Pattern: Over-Splitting

Don't split into tiny fragments:

```
❌ git-commit-types.md (100 tokens)
❌ git-commit-examples.md (100 tokens)
❌ git-commit-format.md (100 tokens)
```

This creates:

- Navigation overhead (which file has what?)
- More total tokens (duplicate headers, context)
- Maintenance burden (sync across files)

**Rule of thumb:** Minimum 500-1000 tokens per file

## Next Steps

1. **Audit your docs:** Find files > 2000 tokens
2. **Identify usage patterns:** What's used together vs separately?
3. **Split by usage:** Rules vs templates, reference vs examples
4. **Test:** Do agents load less context for common tasks?

## Your Project

Review `docs/technical/git-conventions.md`:

- PR templates (lines 201-250) only used when creating PRs
- Conventions (lines 1-200) read frequently for commit guidance
- **Optimization:** Move templates to `docs/technical/templates/`
- **Impact:** 900 tokens saved per convention lookup
