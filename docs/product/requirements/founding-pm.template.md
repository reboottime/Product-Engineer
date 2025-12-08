---
type: requirement
feature: [feature-name-kebab-case]
phase: customer-discovery|poc
owner: founding-product-manager
status: hypothesis|validated|killed
priority: p0|p1|p2
created: YYYY-MM-DD
---

# [Feature Name] - Requirements

> **TL;DR:** [3 sentences: What problem? What's the hypothesis? What does success look like?]

---

## Problem Statement

### User Problem

[1-2 sentences: What specific problem do users face?]

**Evidence:**

- [Research insight or user quote from /docs/product/research/interviews/]
- [Usage data or pain point from customer feedback]
- [Link to research file if exists]

### Why Now?

[1-2 sentences: Why does this matter? What's the impact if we don't solve this?]

---

## Hypothesis

**We believe that** [target user segment]
**Has the problem of** [specific pain point]
**We will know we're right when** [measurable outcome]

---

## User Story

**As a** [user type/persona],
**I want to** [action/capability],
**So that** [benefit/outcome].

### Acceptance Criteria

- [ ] [Specific, testable criterion 1]
- [ ] [Specific, testable criterion 2]
- [ ] [Specific, testable criterion 3]

---

## Solution (MVP)

### Must Have (P0 - Minimum to Test Hypothesis)

- **[Capability 1]:** [Why critical for validation]
- **[Capability 2]:** [Why critical for validation]
- **[Capability 3]:** [Why critical for validation]

### Should Have (P1 - Enhances Learning)

- **[Enhancement 1]:** [How this improves validation]
- **[Enhancement 2]:** [How this improves validation]

### Won't Have (Explicitly Out of Scope)

- **[Capability]:** [Why we're deferring, when we might revisit]
- **[Capability]:** [Why we're deferring, when we might revisit]

---

## Success Metrics

**Primary Metric:** [The ONE metric that proves hypothesis]

| Metric | Target | Measurement |
|--------|--------|-------------|
| [Primary] | [Goal value] | [How we measure] |
| [Secondary] | [Goal value] | [How we measure] |

**Success = ** [Specific criteria, e.g., "20% of users complete core action within first session"]

---

## Validation Plan

**How we'll test:**

1. [Validation method 1 - e.g., "Ship to 50 beta users"]
2. [Validation method 2 - e.g., "Conduct 5 user interviews"]
3. [Validation method 3 - e.g., "Track metrics for 2 weeks"]

**Timeline:** [How long we'll run experiment]

**Decision criteria:** [What results trigger build/iterate/kill decision]

---

## Kill Criteria

We'll kill this feature if:

- [ ] [Criterion 1 - e.g., "<20% completion rate after 2 weeks"]
- [ ] [Criterion 2 - e.g., "No clear problem validation after 3 interviews"]
- [ ] [Criterion 3 - e.g., "Better solution discovered"]

---

## Assumptions

1. [Assumption about users - e.g., "Users check email daily"]
2. [Assumption about behavior - e.g., "Users will share content if friction is low"]
3. [Assumption about constraints - e.g., "Can ship in 1 week"]

**Riskiest assumption:** [Which assumption, if wrong, kills the hypothesis?]

---

## Open Questions

- [ ] **Q1:** [Question that needs answering]
  - **Impact:** [How this affects hypothesis/scope]
  - **How to resolve:** [Interview/prototype/research]

- [ ] **Q2:** [Question that needs answering]
  - **Impact:** [How this affects hypothesis/scope]
  - **How to resolve:** [Interview/prototype/research]

---

## Related Documentation

**Research:** [Link to /docs/product/research/interviews/ or insights/]

**Design:** [Link to /docs/product/design/wireframes/ if exists]

**Decisions:** [Link to /docs/product/decisions/ if exists]

---

## Instructions

1. **Fill YAML** - Enables grep-based discovery
2. **Write TL;DR first** - Forces clarity
3. **Link evidence** - Requirements must be research-backed
4. **Define kill criteria** - Be ready to abandon bad ideas
5. **One primary metric** - Don't dilute focus
6. **Minimum solution** - What's the least we can build to learn?
7. **No engineering specs** - Stay out of technical implementation
8. **Delete this section** when creating actual requirements
