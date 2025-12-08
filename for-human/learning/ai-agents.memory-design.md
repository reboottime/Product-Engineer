# AI Agent Memory Design

Comprehensive guide to designing effective memory systems for AI agents.

---

## What Is Agent Memory?

Agent memory = context files (CLAUDE.md, domain docs) that shape agent behavior, knowledge, and decision-making.

**Why it matters:**

- Determines what agents know and how they act
- Affects token efficiency and performance
- Shapes consistency across conversations
- Enables specialization without duplication

---

## Part 1: Memory Architecture

### Universal vs Domain-Specific

**CLAUDE.md (universal - all agents & claude itself):**

- Communication style (concise, no preambles)
- Folder structure navigation
- Project phase and north star
- Collaboration patterns (TodoWrite, AskUserQuestion)

**Domain docs (specialized - specific agents only):**

- Product strategy, design principles, metrics definitions
- Technical conventions, architecture patterns, API specs
- Git workflows, deployment procedures

**Why separate:**

- Reduces token waste (release manager doesn't need UX frameworks)
- Scales as you add agents (each loads only relevant context)
- Keeps CLAUDE.md lightweight and fast

### Audience Context for Product/Design Agents

**Critical requirement:** PM and Design Lead agents must know WHO they're designing for.

**Without audience context, agents create:**

- Generic solutions that fit no one
- Abstract features divorced from user needs
- Design patterns that don't match user mental models

**How to provide audience context:**

**Option 1: Define in product docs**

```sh
/docs/product/strategy.md
- Target audience: [Who uses this, their context]
- User segments: [Key personas and their goals]
- Key behaviors: [What users actually do]
```

**Option 2: Require upfront in workflow**

- PM agent asks "Who is this for?" before RICE scoring
- Design Lead requires persona/context before wireframing
- Slash commands include audience parameter

**What agents need to know:**

- User tech literacy (affects UI complexity)
- Device/platform usage (mobile-first vs desktop)
- Workflow context (what they're doing when using your product)
- Mental models (how they think about the problem)

**Example - Bad (no audience):**

```
User: "Add a dashboard"
Agent: Creates generic dashboard with lots of charts
```

**Example - Good (audience-aware):**

```
User: "Add a dashboard for busy parents tracking kids' activities"
Agent: Creates mobile-first, glanceable view with quick actions
       (knows: limited time, on-the-go usage, mobile context)
```

### Validation Checklist

**CLAUDE.md stays minimal:**

- [ ] Only universal rules (applies to all agents)
- [ ] No domain-specific frameworks or patterns
- [ ] Points to specialized docs, doesn't duplicate them

**Domain docs are discoverable:**

- [ ] CLAUDE.md "Specialized Agent Context" section lists paths
- [ ] Agent prompts reference specific docs to load
- [ ] Clear naming: `/docs/[domain]/[topic].md`

**Product/Design agents have audience context:**

- [ ] Strategy doc defines target users
- [ ] Workflows require audience input upfront
- [ ] Agents validate "who is this for?" before deciding/designing

---

## Part 2: File Organization

> **⚠️ Accuracy Note:** This section contains claims about Read tool behavior that are partially incorrect. Reality: Read tool has `offset` and `limit` parameters for selective loading. Agents CAN skip sections. The token size recommendations (2000 tokens, 500-1000 tokens) are heuristics not backed by official Claude Code documentation. Use these principles as guidelines, but validate through testing.

### The Misconception

"AI agents can skip irrelevant sections in a file, so keeping everything in one place is fine."

**This is wrong.** (Though agents can use offset/limit for selective loading)

### How Agents Actually Read Files

When an agent uses the Read tool:

1. **Entire file loads** into context (by default)
2. **All tokens processed** (every line costs tokens)
3. **Headings help comprehension, NOT efficiency**
4. **Selective loading possible** - Read tool supports `offset` and `limit` parameters for large files

### Real Example

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

### The Token Math

**Why this matters:**

| Operation | Frequency | Current Cost | Optimized Cost | Savings |
|-----------|-----------|--------------|----------------|---------|
| Check commit rules | 10x/day | 27,000 tokens | 18,000 tokens | 9,000 tokens/day |
| Create PR | 1x/week | 2,700 tokens | 2,400 tokens | 300 tokens/week |

**Net result:** Massive savings on frequent operations, tiny cost on rare ones.

### The Design Principle

**Split files by usage pattern, not just by topic.**

#### Bad: Split by topic

```
docs/
  git.md                    ← Everything git-related
  product.md                ← Everything product-related
```

Result: Agent loads everything when it needs one thing

#### Good: Split by usage + purpose

```sh
docs/technical/
  git-conventions.md        ← Rules (read frequently)
  templates/
    pr-mvp.md              ← Artifacts (read when needed)
```

Result: Agent loads only what it needs

### When to Split Files

**Split when:**

- ✅ Different parts used in different contexts
- ✅ File > 2000 tokens
- ✅ Contains both "rules" and "templates/examples"
- ✅ Some sections rarely needed

**Keep together when:**

- ❌ Always used together
- ❌ File < 1000 tokens
- ❌ Splitting creates more confusion than clarity

### Common Patterns

#### Pattern 1: Rules vs Templates

```
conventions.md     ← How to do it (rules, decisions)
templates/         ← What to generate (artifacts)
```

#### Pattern 2: Reference vs Examples

```
api-spec.md        ← API contracts, rules
examples/          ← Sample requests/responses
```

#### Pattern 3: Strategy vs Tactics

```
strategy.md        ← Why, principles, goals
implementation/    ← How, step-by-step guides
```

### The Clarity Bonus

Smaller files aren't just more efficient - they're clearer:

- **Focused purpose** = easier to understand
- **Less noise** = better signal
- **Faster scanning** = quicker decisions
- **Lower cognitive load** = better comprehension

### Anti-Pattern: Over-Splitting

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

> **Note:** Token size recommendations (2000 tokens, 500-1000 tokens, specific token math examples) are heuristics not backed by official Claude Code documentation. The Read tool supports `offset` and `limit` parameters for selective loading, which contradicts the "no skipping" claim above. Validate these recommendations through empirical testing in your specific context.

---

## Part 3: Content Structure

### TL;DR

AI agent context files (like CLAUDE.md) should follow **Progressive Disclosure**: Context → Constraints → Navigation → Specifics. Early sections set behavioral boundaries before agents act.

### The Pattern

```sh
1. Project Overview      → WHAT/WHY (essential context)
2. Behavioral Rules      → HOW to behave (immediate constraints)
3. Folder Structure      → WHERE things are (navigation foundation)
4. Specific Operations   → DETAILED rules (subset of tasks)
5. Specialized Pointers  → WHERE role-specific docs (navigation)
6. Reference Lists       → WHO/WHAT is available (lookup)
```

### Why This Order Matters

**Agents read sequentially** - Early sections constrain later behavior.

#### Critical: Behavior Before Navigation

**Wrong order:**

```sh
1. Project Overview
2. Folder Structure ← Agent navigates first
3. How to Work      ← Too late - already violated rules
```

**Problem:** Agent might say "Let me thoroughly explain the folder structure..." (verbose, has preamble) before learning communication rules.

**Right order:**

```sh
1. Project Overview
2. How to Work      ← Constraints established FIRST
3. Folder Structure ← Agent navigates with correct behavior
```

**Result:** Agent learns "be concise, no preambles" before taking any action.

### Design Principle

**General → Specific** at each level:

- Context before constraints
- Constraints before navigation
- Whole-project navigation before role-specific
- Common operations before edge cases

### Application

When creating agent context:

1. Start with mission-critical context (what/why/phase)
2. Set behavioral boundaries immediately
3. Provide navigation tools
4. Add operational details
5. Include specialized references
6. End with lookup tables

**The goal:** Agent can't violate important rules because they encounter them before taking action.

### Common Mistakes

**❌ Navigation before behavior:**

```sh
1. Project Overview
2. Folder Structure  ← Too early
3. How to Work       ← Too late
```

Result: Agent navigates with wrong behavior already established.

**❌ Phase buried deep:**

- Phase on line 47 instead of lines 1-10
- Agent may take actions before knowing workflow rules

**❌ Vague behavioral rules:**

- "Be helpful and friendly" (not actionable)
- Should be: "2-3 sentences max, no preambles"

**❌ Duplicating info:**

- Same navigation info in multiple sections
- Increases cognitive load, dilutes important signals

**❌ Critical constraints late:**

- "Never push to main" appears after git workflow examples
- Agent may already be planning wrong approach

### Validation Checklist

**Quick test (first 20 lines):**

- [ ] Can answer: What is this project?
- [ ] Can answer: What phase are we in?
- [ ] Can answer: How should I communicate?
- [ ] Behavioral rules appear before navigation
- [ ] Rules are specific and actionable

**Structure check:**

- [ ] Project Overview in lines 1-15
- [ ] Behavioral rules before line 30
- [ ] Folder structure after behavioral rules
- [ ] Specialized pointers reference concrete file paths
- [ ] No critical info buried after line 100

**Red flags:**

- ⚠️ Abstract principles without concrete examples
- ⚠️ Navigation/tools listed before communication style
- ⚠️ Phase mentioned only once, late in file
- ⚠️ Multiple sections about same topic

### Troubleshooting

**Agent symptom → Likely cause:**

**Verbose responses, has preambles:**

- Behavioral rules came after agent started navigating
- Rules too abstract ("be concise" vs "2-3 sentences max")

**Uses wrong workflow (pushes to main in MVP):**

- Phase not clear in first 10 lines
- Workflow rules appear after examples

**Can't find documentation:**

- Navigation section missing/unclear
- Folder structure doesn't match actual repo
- Specialized pointers missing concrete paths

**Ignores constraints:**

- Rules buried after navigation
- Constraints mixed with optional suggestions
- Not using imperative language ("should" vs "must")

**Asks obvious questions:**

- Project overview too abstract
- Missing concrete examples
- Phase unclear (implies wrong assumptions)

**Fix pattern:**

1. Identify symptom
2. Find where constraint should be
3. Move it earlier (usually before navigation)
4. Make it concrete and actionable
5. Test with fresh agent session

### Research Foundation

**Position Effects (NeurIPS 2023):**

- ["Lost in the Middle"](https://arxiv.org/abs/2307.03172) - Liu et al. found LLM performance degrades when info is in middle vs. beginning
- Early context has stronger influence on behavior

**Ordering Impact (2024 Survey):**

- [Prompt Engineering Survey](https://arxiv.org/abs/2402.07927) - Sahoo et al. survey of prompt engineering techniques
- LLMs highly sensitive to instruction ordering

**Instruction Sensitivity (EMNLP 2024):**

- [Robustness Study](https://aclanthology.org/2024.emnlp-main.33/) - Models prioritize embedded instructions, often focusing on latter parts without full context
- Early instructions set behavioral constraints effectively

**Agent Context Design (NeurIPS 2024):**

- [AutoGuide](https://proceedings.neurips.cc/paper_files/paper/2024/file/d8efbb5dd415974eb095c3f06bff1f48-Paper-Conference.pdf) - Context-aware guidelines in conditional structure improve agent performance

**Verdict:** Progressive Disclosure pattern backed by empirical research on position bias, ordering effects, and instruction sensitivity.

### Epistemic Status

**What's proven (empirical research):**

- Position bias exists - early context influences LLM behavior more (NeurIPS 2023)
- Ordering matters - LLMs sensitive to instruction ordering (2024 Survey)
- Instruction sensitivity - LLMs prioritize early instructions (EMNLP 2024)

**What's reasoned inference (logical application):**

- Applying these principles to agent context file structure
- Specific ordering recommendations (behavior before navigation)
- No formal "agent context design standard" from Anthropic/OpenAI

**Why it's still useful:**

- Built on proven cognitive principles for LLMs
- Logic is sound even without formal codification
- Emerging practice, not established doctrine
- Validate through your own results

**How to use this guide:**

- Apply the pattern as starting point
- Test and observe agent behavior
- Adjust based on your specific needs
- Contribute back what you learn

---

## Part 4: Language Design

### Core Concept

**Agents interpret instructions literally.** Language choice determines whether agents see something as context (optional) or command (mandatory).

### Two Modes

#### Descriptive Language

**Purpose:** Labels and describes content
**Agent interpretation:** "This is information about X"

Examples:

- "Communication Guidelines" → optional patterns
- "How to Work With Human" → background context
- "Best Practices" → suggestions

#### Prescriptive Language

**Purpose:** Commands specific behavior
**Agent interpretation:** "I must do X"

Examples:

- "Follow These Rules" → mandatory directive
- "Universal Agent Rules" → required compliance
- "Never use long prose" → explicit prohibition

### Why This Matters

| Issue | Impact | Solution |
|-------|--------|----------|
| Agents interpret literally | "Guidelines" = flexible, "Rules" = mandatory | Choose words that match intent |
| Ambiguity creates variance | Same instruction → different agent behaviors | Be prescriptive for consistency |
| Headers signal intent | Descriptive header = skippable context | Prescriptive header = must follow |

### Design Principle

**Want guaranteed compliance?** → Use prescriptive language
**Providing optional context?** → Use descriptive language

### Real Examples

**Weak (Descriptive):**

```markdown
## Communication Guidelines
Consider keeping responses concise
```

Agent thinks: "I can be concise if appropriate"

**Strong (Prescriptive):**

```markdown
## Communication Rules
Keep all responses under 3 sentences
```

Agent thinks: "I must stay under 3 sentences"

**Hybrid (Best for headers):**

```markdown
## Universal Agent Rules: Communication
```

Prescriptive intent + descriptive topic = clear mandatory scope

### Testing Your Instructions

Ask: "Could an agent reasonably interpret this as optional?"

- Yes → Add prescriptive language
- No → You're good

### Common Patterns

| Pattern | Type | Effect |
|---------|------|--------|
| "How to..." | Descriptive | Informational |
| "You must..." | Prescriptive | Mandatory |
| "Guidelines for..." | Descriptive | Flexible |
| "Rules for..." | Prescriptive | Required |
| "Consider..." | Descriptive | Optional |
| "Always/Never..." | Prescriptive | Absolute |

### Key Insight

In agentic systems: **Ambiguity = unpredictable behavior**

Every instruction is either a command or context. Choose deliberately.

---

## Part 5: Resources

**External Learning:**

- [Agent Memory Design by Richmond Alake](https://www.youtube.com/watch?v=W2HVdB4Jbjs&t=4s) - Video walkthrough of memory architecture patterns

**Related Guides:**

- `ai-agents.evaluation-framework.md` - 12-dimension checklist for evaluating agent design
- `claude-code.technical-reference.md` - Context loading and tool configuration mechanics

---

## Quick Reference

**Starting a new project?**

1. Define universal context (CLAUDE.md)
2. Split by domain (product/technical/etc)
3. Order: Context → Constraints → Navigation
4. Use prescriptive language for rules

**Optimizing existing agents?**

1. Audit file sizes (split if > 2000 tokens)
2. Check section order (behavior before navigation)
3. Review language (prescriptive for rules)
4. Test: Do agents follow constraints?

**Adding specialized agents?**

1. Create domain-specific docs
2. Keep CLAUDE.md minimal
3. Point agents to relevant docs
4. Include audience context for product agents
