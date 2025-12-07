# Structuring AI Agent Context Files

## TL;DR

AI agent context files (like CLAUDE.md) should follow **Progressive Disclosure**: Context → Constraints → Navigation → Specifics. Early sections set behavioral boundaries before agents act.

## The Pattern

```sh
1. Project Overview      → WHAT/WHY (essential context)
2. Behavioral Rules      → HOW to behave (immediate constraints)
3. Folder Structure      → WHERE things are (navigation foundation)
4. Specific Operations   → DETAILED rules (subset of tasks)
5. Specialized Pointers  → WHERE role-specific docs (navigation)
6. Reference Lists       → WHO/WHAT is available (lookup)
```

## Why This Order Matters

**Agents read sequentially** - Early sections constrain later behavior.

### Critical: Behavior Before Navigation

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

## Design Principle

**General → Specific** at each level:

- Context before constraints
- Constraints before navigation
- Whole-project navigation before role-specific
- Common operations before edge cases

## Application

When creating agent context:

1. Start with mission-critical context (what/why/phase)
2. Set behavioral boundaries immediately
3. Provide navigation tools
4. Add operational details
5. Include specialized references
6. End with lookup tables

**The goal:** Agent can't violate important rules because they encounter them before taking action.

## Common Mistakes

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

## Validation Checklist

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

## Troubleshooting

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

## Research Foundation

**Position Effects (NeurIPS 2023):**

- ["Lost in the Middle"](https://arxiv.org/abs/2307.03172) - Liu et al. found LLM performance degrades when info is in middle vs. beginning
- Early context has stronger influence on behavior

**Ordering Impact (2024 Survey):**

- [Prompt Engineering Survey](https://arxiv.org/abs/2402.07927) - Sahoo et al. found reordering examples produced **40%+ accuracy shifts**
- LLMs highly sensitive to instruction ordering

**Instruction Sensitivity (EMNLP 2024):**

- [Robustness Study](https://aclanthology.org/2024.emnlp-main.33/) - Models prioritize embedded instructions, often focusing on latter parts without full context
- Early instructions set behavioral constraints effectively

**Agent Context Design (NeurIPS 2024):**

- [AutoGuide](https://proceedings.neurips.cc/paper_files/paper/2024/file/d8efbb5dd415974eb095c3f06bff1f48-Paper-Conference.pdf) - Context-aware guidelines in conditional structure improve agent performance

**Verdict:** Progressive Disclosure pattern backed by empirical research on position bias, ordering effects, and instruction sensitivity.

## Epistemic Status

**What's proven (empirical research):**

- Position bias exists - early context influences LLM behavior more (NeurIPS 2023)
- Ordering matters - 40%+ performance swings from reordering (2024 Survey)
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
