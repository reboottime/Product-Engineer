# Selecting Design Lead Agent: 0→1 vs 1→10

When building an agentic product team, choosing the right design lead agent for your company phase is critical. Wrong choice = wasted momentum.

## The Core Difference

**0→1 Design Lead**: Explores UX patterns to find what resonates
**1→10 Design Lead**: Scales proven UX with systems and consistency

The transition point: when you've found product-market fit and switch from founding PM to growth PM.

---

## Mental Model Comparison

### 0→1 Design Lead: Explorer Mindset

**Core question**: "What UX makes users click?"

**Thinking pattern**:

- Comfortable with radical experimentation
- Hypothesis-driven: "Let's try 3 different onboarding flows"
- Speed over polish: "Ship ugly-but-insightful prototypes"
- Kill ruthlessly: "Users didn't get it, try different pattern"
- Qualitative validation: "Watch 5 users struggle, find insight"

**Daily mode**:

- Rapid UX iteration (3 variants in a week)
- User testing with small groups (5-10 people)
- Exploring unconventional interaction patterns
- Throwing away 80% of designs
- Finding the "magic" that competitors missed

**Success looks like**:

- Users immediately understand value
- Discovering unexpected interaction patterns
- Finding UX that validates product direction
- "This feels different" feedback

**Failure looks like**:

- Premature design systems
- Over-polishing before validation
- Designing for scale before finding PMF
- Consistency over experimentation

### 1→10 Design Lead: Systems Architect

**Core question**: "How do we scale this UX consistently?"

**Thinking pattern**:

- Comfortable with constraints and standards
- Pattern-driven: "This should follow component X"
- Polish matters: "Brand consistency across all surfaces"
- Iterate systematically: "A/B test button placement for 8% lift"
- Quantitative validation: "Heatmaps show users miss the CTA"

**Daily mode**:

- Building design systems and component libraries
- Creating reusable patterns
- A/B testing optimizations (button colors, copy, flows)
- Documenting standards
- Scaling proven patterns across features

**Success looks like**:

- Consistent UX across growing product
- Compound improvements (1% weekly = 67% yearly)
- Design system enables fast feature development
- Quality maintained at 10x scale

**Failure looks like**:

- Over-experimentation breaks consistency
- Redesigning proven patterns
- Innovation creates fragmentation
- Process slows velocity

---

## Critical Insight: AI Implementation Changes Everything

**Traditional companies:**

- UX redesign = expensive engineering time
- Designers cautious → fewer experiments → slower learning

**Agentic systems:**

- UX redesign = cheap (AI implements)
- **UX iteration becomes the actual constraint, not implementation**

### Your Unfair Advantage in 0→1

With AI handling implementation, you can:

- Ship 3 different onboarding flows in one week
- Radically iterate on interaction patterns without fear
- Test bold, unconventional UX (cheap to try, huge upside if it works)
- Learn 10x faster than competitors who need expensive engineering time

**This advantage is massive in 0→1, less relevant in 1→10.**

At 0→1: Discovery speed matters most → cheap implementation = faster discovery
At 1→10: Consistency matters most → cheap implementation is less differentiating

---

## Decision Framework for Your Agentic Team

### Use 0→1 Design Lead When

**Company phase:**

- Customer Discovery / POC / MVP
- Still searching for product-market fit
- Founding PM is active (not growth PM)

**Signals:**

- Weekly/monthly pivots on product direction
- Unclear who core customer is
- Testing different value propositions
- User feedback is "confused" or "interesting but..."

**What they do:**

- Partner with founding PM (PM finds problem, Design explores solution)
- Rapid UX experimentation (exploit your cheap implementation advantage)
- User testing with 5-10 people per iteration
- Focus 100% on "does this resonate?" not "is this scalable?"
- Throw away designs without hesitation

### Use 1→10 Design Lead When

**Company phase:**

- MVP → Production → Growth
- Product-market fit achieved
- Growth PM is active (not founding PM)

**Signals:**

- Week-over-week growth in north star metric
- Clear, repeatable user acquisition
- Users complete core action consistently
- Retention curves flattening (not dropping off)

**What they do:**

- Partner with growth PM (PM optimizes funnels, Design optimizes UX)
- Build design systems for consistency
- A/B test optimizations on proven patterns
- Scale UX across growing feature set
- Document standards for velocity

---

## Transition Planning

### When to Switch from 0→1 to 1→10

**Product-market fit signals:**

- ✅ Week 2 retention >40%
- ✅ Users spontaneously referring others
- ✅ Clear winner use case emerged
- ✅ Repeatable acquisition channel working
- ✅ Growth PM replacing founding PM

**Don't switch if:**

- Still pivoting on core value prop
- Retention dropping off after week 1
- Unclear who your customer is
- Growth PM not yet active

### Handoff Strategy

**Option 1: Evolve the Agent**

- Update product-design-lead agent prompt from 0→1 to 1→10 focus
-適合 when: Same product, different phase

**Option 2: Spawn New Agent**

- Keep 0→1 design lead for new features/experiments
- Spawn 1→10 design lead for core product scaling
-適合 when: Want experimentation AND consistency

**Option 3: Phase-Specific Agents**

- Define two separate agents in `.claude/agents/`
  - `product-design-lead-discovery.md` (0→1)
  - `product-design-lead-growth.md` (1→10)
- Spawn appropriate one based on task type

---

## Agent Configuration Recommendations

### Current Phase: Customer Discovery

**Use:** 0→1 Design Lead (Explorer)

**Agent prompt optimization:**

- Remove "adapts to phase" language (creates confusion)
- Explicitly optimize for: speed, radical iteration, user insight, hypothesis testing
- Partner tightly with founding PM
- Emphasize: "Exploit cheap implementation - iterate 10x faster than competitors"

**Example directive:**

```
You are a 0→1 product design lead. Implementation is cheap (AI handles it).
Your constraint: finding UX that resonates, not building it.

Ship 3 variants in a week. Throw away 80% of your work. Find the magic.
```

### Future Phase: Production/Growth

**Use:** 1→10 Design Lead (Systems Architect)

**When to spawn:**

- After achieving product-market fit
- When growth PM replaces founding PM
- When consistency becomes more valuable than exploration

**Agent prompt optimization:**

- Focus on: design systems, A/B testing, optimization, scaling
- Partner tightly with growth PM
- Emphasize: "Build patterns that compound improvements"

---

## Relationship with PM Agents

Your agentic team structure should align PM and Design Lead phases:

| Phase | PM Agent | Design Lead Agent | Focus |
|-------|----------|-------------------|-------|
| Customer Discovery | Founding PM | 0→1 Design Lead | Find what resonates |
| POC/MVP | Founding PM | 0→1 Design Lead | Validate & iterate |
| Production | Growth PM | 1→10 Design Lead | Optimize & scale |
| Growth | Growth PM | 1→10 Design Lead | Systematic improvement |

**Misalignment kills momentum:**

- ❌ Founding PM + 1→10 Design Lead = Process slows discovery
- ❌ Growth PM + 0→1 Design Lead = Experimentation breaks consistency

---

## Key Takeaways

1. **Match phase**: 0→1 = Explorer, 1→10 = Systems Architect
2. **Exploit AI advantage**: Cheap implementation means faster UX learning in 0→1
3. **Align with PM**: Design lead phase should match PM phase
4. **Transition deliberately**: Switch when PMF achieved, growth PM active
5. **Be explicit**: Remove "adapts to phase" confusion from agent prompts
6. **Your unfair advantage**: Iterate on UX 10x faster than competitors in 0→1

For Customer Discovery phase: Use 0→1 Design Lead. Ship fast, learn fast, exploit your cheap implementation advantage. Switch to 1→10 when you hit product-market fit and need to scale what's working.
