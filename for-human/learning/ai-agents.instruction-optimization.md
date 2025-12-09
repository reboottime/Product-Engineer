# AI Agent Instruction Optimization

Guide for writing efficient, effective AI agent instruction documents. Use this when creating or refining agent prompts to maximize signal while minimizing token usage.

---

## Context

This framework optimizes AI agent instructions for production use. Agents learn patterns from examples, not repetition - optimize for clarity and actionability over explanation.

**Example use case:** A founding product design lead agent that ships 3 UX variants/week, challenges weak decisions, tests early, and iterates ruthlessly.

---

## Optimization Principles

### 1. Token Efficiency

**Goal:** Maximum signal, minimum tokens

- Remove redundant explanations (agent learns patterns, not repetition)
- Collapse similar rules into single statements
- Cut examples that don't add unique patterns

**Test:** Does this rule teach a new pattern? No → remove

---

### 2. Decision Clarity

**Goal:** Sharp boundaries between autonomy, consultation, escalation

- Keep decision boundaries sharp (autonomy vs. consult vs. escalate)
- Merge overlapping rules under clearer categories
- Remove "why" explanations that are obvious from context

**Test:** Can agent quickly determine decision authority? No → clarify

---

### 3. Actionable Compression

**Goal:** Instructions that drive action, not understanding

- **Workflows:** Steps only, cut process commentary
- **Templates:** Keep (used directly), cut teaching text
- **Principles:** Distill to memorable rules

**Test:** Does agent need this to execute? No → remove

---

### 4. Signal Preservation

**Goal:** Keep what changes behavior, cut what doesn't

**Keep:**

- Authority boundaries
- Specific metrics
- Concrete workflows
- Templates

**Cut:**

- Motivational text
- Philosophy
- Redundant examples

**Test:** Does removing this change agent behavior? No → remove

---

### 5. Structural Scan

**Goal:** Optimal information architecture

- Frontload critical rules (boundaries, authority)
- Collapse redundant sections
- Tables for reference data

**Test:** Can agent scan and find rules quickly? No → restructure

---

## Application Workflow

**When creating new agent instructions:**

1. Write draft with full context
2. Apply optimization principles (1-5)
3. Test with agent (check behavior matches intent)
4. Remove sections that didn't change behavior
5. Iterate until minimal viable instruction set

**When refining existing instructions:**

1. Identify behavior gaps (agent confused? over-asking?)
2. Map to optimization principle
3. Fix specific issue
4. Test behavior change
5. Remove anything that didn't help

---

## Examples

### Before Optimization

```
When you encounter a design decision, you should think carefully about
whether this is something you can decide on your own, or whether you
need to consult with the human. Generally speaking, you should be able
to make decisions about visual design elements like colors and spacing,
but you should consult with the human about major UX flow changes that
could impact the user experience significantly.
```

**Token count:** ~70 tokens

### After Optimization

```
**Autonomous:** Visual design (colors, spacing, typography)
**Consult:** Major UX flow changes
```

**Token count:** ~15 tokens
**Behavior:** Identical

---

## Measuring Success

**Good optimization:**

- 30-50% token reduction
- Same or better agent behavior
- Faster agent decision-making
- Clearer boundaries

**Over-optimization:**

- Agent confusion increases
- More clarifying questions
- Behavior degrades
- Lost critical context

**Balance:** Minimum tokens that preserve full behavioral fidelity

---

## Related

- `/for-human/learning/ai-agents.evaluation-framework.md` - Evaluate agent quality
- `/for-human/learning/ai-agents.memory-design.md` - Design agent memory systems
