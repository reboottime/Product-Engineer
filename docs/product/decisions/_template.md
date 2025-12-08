---
type: decision
decision_type: validation|prioritization|scope|integration|other
feature: [feature-name-kebab-case]
phase: customer-discovery|poc|mvp|production
owner: product-manager
status: draft|review|approved|implemented|superseded
stakeholders: [founding-product-manager, tech-lead, founding-product-design-lead]
impact: high|medium|low
supersedes: []
last_updated: YYYY-MM-DD
created: YYYY-MM-DD
---

# [Feature/Topic] - [Decision Type]

**Date:** YYYY-MM-DD

> **TL;DR:** [3 sentences: What did we decide? Why? What's the impact?. It has to be comprehensible like a new way]

---

## Context

**Problem/Question:**
[What decision needed to be made? What was the trigger for this decision?]

**Background:**
[Relevant context: market conditions, user feedback, business goals, technical constraints]

**Timing:**
[Why are we making this decision now? What's the deadline or forcing function?]

**Constraints:**
- [Time constraint]
- [Budget constraint]
- [Technical constraint]
- [Resource constraint]

---

## Decision

**We decided to:** [Clear statement of the decision]

**Scope:**
- **In scope:** [What this decision covers]
- **Out of scope:** [What this decision doesn't cover]

**Timeline:** [When this takes effect, when it should be reviewed]

---

## Rationale

### Decision Matrix

| Criteria | Weight | Option 1: [Name] | Option 2: [Name] | Option 3: [Name] | Chosen Option |
|----------|--------|------------------|------------------|------------------|---------------|
| [Criterion 1] | High | 8/10 | 6/10 | 4/10 | Option 1 |
| [Criterion 2] | Medium | 5/10 | 8/10 | 7/10 | Option 2 |
| [Criterion 3] | High | 7/10 | 5/10 | 9/10 | Option 3 |
| **Total Score** | | **20** | **19** | **20** | **Option 1** |

**Scoring Guide:** 1-10 scale (1=poor, 10=excellent)

### Why This Decision

1. **[Primary reason]:** [Explanation with evidence]
2. **[Secondary reason]:** [Explanation with evidence]
3. **[Tertiary reason]:** [Explanation with evidence]

### Supporting Evidence

- **User research:** [Link to research/YYYY-MM-DD-[topic].md or key insight]
- **Competitive analysis:** [Link to competitive/[topic].md or key finding]
- **Data:** [Usage data, metrics, analytics supporting decision]
- **Expert input:** [Technical feasibility from tech-lead, design input, etc.]

---

## Alternatives Considered

### Option 1: [Name]

**Description:** [What this option entailed]

**Pros:**
- [Advantage 1]
- [Advantage 2]

**Cons:**
- [Disadvantage 1]
- [Disadvantage 2]

**Why not chosen:** [Specific reason]

---

### Option 2: [Name]

**Description:** [What this option entailed]

**Pros:**
- [Advantage 1]
- [Advantage 2]

**Cons:**
- [Disadvantage 1]
- [Disadvantage 2]

**Why not chosen:** [Specific reason]

---

## Consequences

### Positive Impacts

| Impact Area | Description | Magnitude |
|-------------|-------------|-----------|
| User Experience | [How this improves UX] | High |
| Development Speed | [How this affects dev] | Medium |
| Business Metrics | [Impact on metrics] | High |

### Negative Impacts / Trade-offs

| Trade-off | Description | Mitigation |
|-----------|-------------|------------|
| [Area of concern] | [What we're sacrificing] | [How we'll minimize impact] |
| [Area of concern] | [What we're sacrificing] | [How we'll minimize impact] |

### Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| [Risk 1] | High/Med/Low | High/Med/Low | [How we'll address] |
| [Risk 2] | High/Med/Low | High/Med/Low | [How we'll address] |

---

## Action Items

- [ ] **[Owner]:** [Specific action] by [date]
- [ ] **[Owner]:** [Specific action] by [date]
- [ ] **[Owner]:** [Specific action] by [date]

---

## Review & Re-evaluation

**Review Date:** [When we should revisit this decision]

**Triggers for re-evaluation:**
- [Condition that would make us reconsider]
- [Metric threshold that would trigger review]
- [External factor that would change context]

**Success Criteria:**
- [How we'll know if this was the right decision]
- [Metrics to track]

---

## Related Documentation

**Requirements:**
- [Link to requirements/[feature].md if this decision affects requirements]

**Designs:**
- [Link to design docs if this decision affects design]

**Research:**
- [Link to research/YYYY-MM-DD-[topic].md that informed this decision]

**Competitive Analysis:**
- [Link to competitive/[topic].md if relevant]

**Technical Documentation:**
- [Link to technical/adr/ADR.[topic].md if technical implications]

**Previous Decisions:**
- **Supersedes:** [Link to decision this replaces]
- **Related to:** [Link to related decisions]

---

## Stakeholder Sign-off

| Stakeholder | Role | Status | Date |
|-------------|------|--------|------|
| [Name] | Product Manager | Approved | YYYY-MM-DD |
| [Name] | Tech Lead | Approved | YYYY-MM-DD |
| [Name] | Product Design Lead | Approved | YYYY-MM-DD |

---

## Instructions for Using This Template

**Decision Types:**
- **validation** - Should we build this feature? (based on user research)
- **prioritization** - What should we build next and why?
- **scope** - What's in/out of scope for a feature?
- **integration** - Which third-party service/tool to use?
- **other** - Other product decisions

**When to create a decision doc:**
- Feature validation (based on user research)
- Quarterly/monthly prioritization
- Choosing between multiple approaches
- Major scope changes
- Integration/vendor selection
- Process changes

**Tips:**
1. **Be decisive** - State the decision clearly, don't hedge
2. **Show your work** - Decision matrix makes reasoning transparent
3. **Document alternatives** - Helps future team understand trade-offs
4. **Link bidirectionally** - If you reference a requirement, update that requirement to reference this decision
5. **Set review dates** - Decisions aren't permanent, plan to revisit
6. **Date-first filename** - Decisions are time-bound: `2025-11-15-auth-magic-link.md`
7. **Delete this section** when creating actual decision docs