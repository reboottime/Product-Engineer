# LLM-Optimized Documentation Framework

**Purpose:** Methodology for creating minimal, high-signal documentation optimized for LLM consumption.

**Core Principle:** **Keep only what the LLM doesn't already know from training. Remove everything else.**

---

## Optimization Methodology

### The Knowledge Test (Primary Filter)

For every section, ask: **"Does the LLM already know this from training data?"**

| Content Type | LLM Knows? | Action | Reason |
|--------------|------------|--------|--------|
| React hooks (useState, useEffect) | ✅ Yes | ❌ Remove | Covered in training data |
| Next.js App Router fundamentals | ✅ Yes | ❌ Remove | Official docs in training |
| Generic best practices | ✅ Yes | ❌ Remove | Universal knowledge |
| Zod validation basics | ✅ Yes | ❌ Remove | Library docs in training |
| **Your Supabase setup** | ❌ No | ✅ **Keep** | Project-specific |
| **Your auth pattern** (`getUser` not `getSession`) | ❌ No | ✅ **Keep** | Project convention |
| **Your return type** (`{ success, error?, data? }`) | ❌ No | ✅ **Keep** | Project convention |
| **Your file organization** (`app/actions/*.ts`) | ❌ No | ✅ **Keep** | Project-specific |
| **iOS Safari gotchas** (button types) | ❌ No | ✅ **Keep** | Rare edge case |

### Evaluation Framework

```sh
┌─ Read section
│
├─ Q1: Is this explaining what a framework/library does?
│  └─ YES → Remove (LLM knows React, Next.js, Zod, etc.)
│  └─ NO → Continue
│
├─ Q2: Is this a generic best practice?
│  └─ YES → Remove (LLM knows "validate user input", "handle errors", etc.)
│  └─ NO → Continue
│
├─ Q3: Are there multiple examples of the same pattern?
│  └─ YES → Keep 1 best example, remove others
│  └─ NO → Continue
│
├─ Q4: Is this YOUR project's specific implementation?
│  └─ YES → Keep (conventions, setup, gotchas)
│  └─ NO → Remove
│
└─ Q5: Can you reduce this further without losing critical info?
   └─ YES → Repeat process
   └─ NO → Done ✅
```

---

## Reduction Metrics

### Target Reductions by Doc Type

| Doc Type | Target Reduction | Length Target | What to Keep |
|----------|------------------|---------------|--------------|
| Pattern/Guide docs | 60-80% | 100-250 lines | Project patterns only |
| Reference docs | 40-60% | 100-250 lines | Code templates + conventions |
| Architecture docs | 20-40% | 150-250 lines | Trees + decisions |
| Troubleshooting | 50-70% | 80-150 lines | Project gotchas only |

### Signal-to-Noise Calculation

```
Signal = Project-specific knowledge (conventions, gotchas, decisions)
Noise = Generic explanations, redundant examples, verbose prose

Baseline (typical docs): 30% signal, 70% noise
Target (optimized): 90% signal, 10% noise
```

**How to measure:**

1. Count lines of project-specific content
2. Count lines of generic explanations
3. Calculate: `Signal % = (project lines / total lines) * 100`
4. Iterate until Signal % ≥ 90%

---

## Optimization Process (6 Steps)

### Step 1: Audit Current State

For each file, record:

```markdown
File: [name.md]
- Current lines: [X]
- Estimated generic content: [Y%]
- Estimated project-specific: [Z%]
- Redundant examples: [count]
- Verbose explanations: [count sections]
- **Verdict**: Can reduce to ~[N] lines ([R%] reduction)
```

**Example:**

```markdown
File: patterns.server-actions-advanced.md
- Current lines: 1,041
- Estimated generic: 70% (React 19 hooks, Next.js basics)
- Estimated project-specific: 30% (Supabase patterns, conventions)
- Redundant examples: 8+ (multiple useActionState examples)
- Verbose explanations: 15+ sections
- **Verdict**: Can reduce to ~250 lines (76% reduction)
```

### Step 2: Extract Unique Knowledge

Create a "Keep List" of project-specific knowledge:

```markdown
✅ KEEP (Project-Specific):
- Supabase client setup: `createClient()` from `@/lib/supabase/server`
- Auth pattern: Always `getUser()` not `getSession()` (security)
- Return convention: `{ success: boolean, error?: string, data?: T }`
- Revalidation rule: Call before redirect
- File location: `app/actions/[feature].ts` with `'use server'`
- iOS Safari gotcha: `type="button"` for non-submit buttons
- Your Suspense + Promise.all pattern for parallel fetching

❌ REMOVE (Generic/LLM Knows):
- What useActionState is and how it works
- General form validation concepts
- Why Server Actions are better than API routes
- React 19 hooks explanation
- Next.js revalidation fundamentals
- Multiple examples of same pattern (keep 1)
```

### Step 3: Create Minimal Reference

Use this template:

```markdown
---
title: [Topic] Reference
type: reference
use_cases: [case1, case2, case3]
last_updated: YYYY-MM-DD
---

# [Topic] Reference

> **For LLMs:** Load when [specific scenario - 1 sentence].

## Standard Template

```language
// Your project's standard pattern
// Code with inline comments showing conventions
```

## Patterns

### [Pattern 1 Name]

```language
// Minimal code showing YOUR implementation
```

### [Pattern 2 Name]

```language
// Minimal code showing YOUR implementation
```

## Project Conventions (Critical)

- **[Convention 1]**: [Brief, specific rule]
- **[Convention 2]**: [Brief, specific rule]
- **[Convention 3]**: [Brief, specific rule]

## Decision Tree

| User Need | Pattern | Hook/Tool |
|-----------|---------|-----------|
| [Need 1] | [Pattern 1] | [If applicable] |
| [Need 2] | [Pattern 2] | [If applicable] |

## Related Docs

- **[Related 1]**: `file-name.md`
- **[Related 2]**: `file-name.md`

```

**Rules:**
- 70%+ code, 30% prose
- Max 1 example per pattern
- No framework explanations
- Project conventions only

### Step 4: Create Troubleshooting (If Needed)

Only include **project-specific gotchas**:

```markdown
---
title: [Topic] Troubleshooting
type: troubleshooting
---

# [Topic] Troubleshooting

> **For LLMs:** Load when [topic] not working.

## Issue: [Specific Problem]

**Symptom:** [What they see]

**Cause:** [Project-specific reason]

**Fix:**
```language
// Minimal fix code
```

**Related:** `reference.topic.md` (section: "Pattern")

---

## Issue: [Next Problem]

[Repeat format for 5-10 common issues]

```

### Step 5: Create Index/Router

```markdown
---
title: [Section] Index
type: index
---

# [Section] Index

> **For LLMs:** Documentation router.

## Quick Decision Tree

| User Request | Load This File |
|-------------|----------------|
| [Request 1] | `reference.topic1.md` |
| [Request 2] | `reference.topic2.md` |
| [Not working] | `troubleshooting.topic.md` |

## Available References

### [Topic 1]
- **reference.topic1.md** - [1-2 sentences]
  - [Key features]

## Glob Patterns

```bash
# All references
docs/section/reference.*.md

# All troubleshooting
docs/section/troubleshooting.*.md
```

```

### Step 6: Archive & Update

1. **Archive old files:**
   ```bash
   mkdir -p docs/section/archived
   mv docs/section/old-verbose.md docs/section/archived/
   ```

2. **Update cross-references:**
   - Search codebase for old file references
   - Update CLAUDE.md or main index
   - Update related docs

3. **Measure improvement:**
   - Record before/after metrics
   - Calculate reduction percentage
   - Verify signal-to-noise improvement

---

## Quality Checklist

Before calling documentation "optimized", verify:

### ✅ Content Quality

- [ ] Zero generic framework/library explanations
- [ ] Every pattern is YOUR project's specific implementation
- [ ] No redundant examples (max 1 per pattern)
- [ ] Code-heavy (70%+ code, 30% prose)
- [ ] Decision trees replace "when to use" essays
- [ ] No sections that can be reduced further

### ✅ Structure Quality

- [ ] YAML frontmatter with `type` and `use_cases`
- [ ] "For LLMs:" directive at top
- [ ] Clear sections (Template → Patterns → Conventions → Decision Tree)
- [ ] Cross-references (no duplicate content)
- [ ] Glob-friendly naming (`reference.*`, `troubleshooting.*`)

### ✅ Length Quality

- [ ] Reference files: 100-250 lines
- [ ] Troubleshooting: 80-150 lines
- [ ] Index: 80-120 lines
- [ ] Each file is "irreducible" (can't cut without losing critical info)

### ✅ Discoverability Quality

- [ ] Index acts as router
- [ ] File names indicate purpose
- [ ] Decision trees in every reference
- [ ] Clear use_cases in frontmatter
- [ ] Glob patterns documented

---

## Real-World Example: Server Actions

### Before Optimization

```
Files: 3
- patterns.server-actions.md (364 lines)
- patterns.server-actions-advanced.md (1,041 lines)
- reference.server-actions.md (388 lines)

Total: 1,793 lines
Generic content: ~70%
Signal-to-noise: 30:70
```

### Audit Findings

```markdown
Generic content to remove:
- React 19 hooks explanations (~400 lines)
- Next.js fundamentals (~200 lines)
- "What are Server Actions" (~150 lines)
- Multiple useActionState examples (~180 lines)
- Best practices essays (~200 lines)
- Duplicate patterns across files (~150 lines)

Project-specific to keep:
- Supabase createClient() pattern
- getUser() vs getSession() convention
- Return type { success, error?, data? }
- File location app/actions/*.ts
- revalidatePath() before redirect rule
- iOS Safari button type gotcha
- Zod integration pattern
```

### After Optimization

```
Files: 1
- reference.server-actions.md (249 lines)

Total: 249 lines (86% reduction)
Generic content: ~10%
Signal-to-noise: 90:10
```

### What Changed

**Removed:**

- All React/Next.js explanations (LLM knows)
- Verbose "why" essays (keep "how" only)
- 7 duplicate useActionState examples (kept 1)
- Generic best practices
- Long introductions

**Kept:**

- Standard template with YOUR auth/error/revalidation
- 6 patterns showing YOUR implementation
- Project conventions (critical gotchas)
- Decision tree (which pattern when)
- Cross-references

**Result:**

- 1/7th the size
- 3x more signal
- Faster for LLM to parse
- Easier to maintain

---

## Common Mistakes

### ❌ Don't Do This

**1. Keeping Generic Examples**

```markdown
❌ BAD:
"useState is a React hook that allows you to add state to functional components.
Here's how it works..."

✅ GOOD:
[Just show YOUR usage in code]
```

**2. Multiple Examples of Same Concept**

```markdown
❌ BAD:
Example 1: useActionState for login
Example 2: useActionState for signup
Example 3: useActionState for profile update
Example 4: useActionState for settings
Example 5: useActionState for password reset

✅ GOOD:
[One example showing YOUR standard pattern]
```

**3. Verbose Explanations**

```markdown
❌ BAD:
"Server Actions are a new feature introduced in Next.js 13 that enable
server-side data mutations without creating API routes. They provide
better type safety and..."

✅ GOOD:
[Jump straight to code pattern]
```

**4. Duplicate Content**

```markdown
❌ BAD:
// Same auth pattern in server-actions.md
export async function action() {
  const { data: { user } } = await supabase.auth.getUser()
  if (!user) return { error: 'Not authenticated' }
}

// Same auth pattern in server-components.md
export async function Component() {
  const { data: { user } } = await supabase.auth.getUser()
  if (!user) redirect('/login')
}

✅ GOOD:
// In server-actions.md
[Show pattern once]

// In server-components.md
"For auth pattern, see reference.server-actions.md"
```

**5. Generic Best Practices**

```markdown
❌ BAD:
- Always validate user input
- Handle errors gracefully
- Provide user feedback
- Use TypeScript for type safety

✅ GOOD:
- Auth: Always `getUser()` not `getSession()` (security - RLS bypass risk)
- Returns: `{ success: boolean, error?: string, data?: T }`
- iOS Safari: `type="button"` for non-submit buttons (auto-submits otherwise)
```

---

## Maintenance Strategy

### When to Update Docs

| Trigger | Action |
|---------|--------|
| New project pattern | Add to reference (if ≠ existing patterns) |
| New gotcha discovered | Add to troubleshooting |
| Convention changes | Update ALL affected references |
| Framework updates | ONLY update if YOUR usage changes |

### Monthly Review Process

```markdown
1. [ ] Check for new patterns in codebase (git log, PR reviews)
2. [ ] Verify conventions still accurate (auth, returns, file locations)
3. [ ] Test: Can LLM find info in <30 seconds?
4. [ ] Prune: Any sections that became generic knowledge?
5. [ ] Expand: New troubleshooting issues from team?
6. [ ] Measure: Still at 90:10 signal-to-noise?
```

### Growth Rules

**Add new doc when:**

- New major feature with ≥3 unique patterns
- Existing doc would exceed 300 lines
- Topic orthogonal to existing docs
- Platform-specific issue needs dedicated troubleshooting

**Update existing when:**

- Small pattern variation
- Additional convention/gotcha
- Related to existing patterns
- Under 300 lines after update

**Split existing when:**

- File exceeds 400 lines
- Covers 5+ unrelated topics
- Can cleanly divide by use case
- Multiple decision trees needed

---

## Success Metrics

Documentation is optimized when you achieve:

| Metric | Target | Measurement |
|--------|--------|-------------|
| Line reduction | 50-80% | (Before - After) / Before × 100 |
| Signal-to-noise | 90:10 | Project-specific lines / Total lines |
| Generic content | <10% | Generic explanation lines / Total lines |
| File length | <250 lines | Line count per reference file |
| Redundancy | 0 | Duplicate patterns across files |
| Irreducibility | 100% | Can't remove anything without losing critical info |

### Example Metrics

```markdown
## Server Actions Optimization Results

Before:
- Files: 3
- Total lines: 1,793
- Generic content: ~70%
- Average file: 598 lines
- Redundancy: High (same patterns in multiple files)

After:
- Files: 1
- Total lines: 249
- Generic content: ~10%
- Average file: 249 lines
- Redundancy: Zero

Improvement:
- Line reduction: 86%
- Signal increase: 60% points (30% → 90%)
- Noise reduction: 88% ((70% → 10%) / 70%)
- Context window savings: 7x smaller
```

---

## Quick Reference

### Optimization Decision Flow

```
File → Audit → Extract → Create Minimal → Archive → Update Cross-refs

Audit Questions:
1. What % is generic? (Target: <10%)
2. What % is project-specific? (Target: >90%)
3. How many redundant examples? (Target: 1 per pattern max)
4. Can it be split into smaller files? (Target: <250 lines each)

Extraction Checklist:
- [ ] List all project conventions
- [ ] List all gotchas/edge cases
- [ ] Identify 1 best example per pattern
- [ ] Note cross-references needed

Creation Rules:
- Code > Prose (70:30 ratio)
- Show > Tell (patterns > explanations)
- Specific > Generic (YOUR impl > theory)
- Concise > Verbose (decision tree > essay)
```

### File Structure Template

```
docs/section/
├── index.md                    # Router (80-120 lines)
├── reference.topic1.md         # Patterns (100-250 lines)
├── reference.topic2.md         # Patterns (100-250 lines)
├── troubleshooting.topic.md    # Issues (80-150 lines)
├── compatibility.platform.md   # Gotchas (50-100 lines)
└── archived/                   # Old docs
    └── verbose-old-doc.md
```

---

## Remember

> **If the LLM already knows it from training, you don't need to document it.**
>
> **Only document what makes YOUR project unique.**

Focus areas for documentation:

1. ✅ Your setup/configuration
2. ✅ Your conventions/patterns
3. ✅ Your gotchas/edge cases
4. ✅ Your decisions (why this vs that)
5. ❌ NOT: Framework basics
6. ❌ NOT: Generic best practices
7. ❌ NOT: "How X works" explanations

**The goal:** Every line in your docs should answer "How do WE do this?" not "What is this?"
