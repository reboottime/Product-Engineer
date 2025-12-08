---
type: requirement
feature: [feature-name-kebab-case]
phase: customer-discovery|poc|mvp|production
owner: product-manager
status: draft|review|approved|implemented|deprecated
priority: p0|p1|p2|p3
validated: true|false
dependencies: []
related_designs: []
related_decisions: []
last_updated: YYYY-MM-DD
created: YYYY-MM-DD
---

# [Feature Name] - Requirements

> **TL;DR:** [3 sentences: What problem does this solve? What's the solution? What does success look like?]

---

## Problem Statement

### User Problem

[1-2 sentences: What specific problem do users face? Include evidence from research.]

**Evidence:**

- [Research insight or user quote from research/[date]-[topic].md]
- [Usage data or pain point from customer feedback]

### Business Problem

[1-2 sentences: Why does this matter to the business? What's the impact if we don't solve this?]

**Impact:**

- [Revenue/Retention/Acquisition impact]
- [Strategic importance or competitive necessity]

---

## User Story

**As a** [user type/persona],
**I want to** [action/capability],
**So that** [benefit/outcome].

### Acceptance Criteria

- [ ] [Specific, testable criterion 1]
- [ ] [Specific, testable criterion 2]
- [ ] [Specific, testable criterion 3]
- [ ] [Specific, testable criterion 4]

---

## Functional Requirements

### Must Have (P0 - Critical for MVP)

| Req ID | Requirement | Rationale |
|--------|-------------|-----------|
| F1 | [Specific capability] | [Why this is critical] |
| F2 | [Specific capability] | [Why this is critical] |
| F3 | [Specific capability] | [Why this is critical] |

### Should Have (P1 - High Priority)

| Req ID | Requirement | Rationale |
|--------|-------------|-----------|
| F4 | [Enhancement] | [Why this adds value] |
| F5 | [Enhancement] | [Why this adds value] |

### Nice to Have (P2 - Post-MVP)

| Req ID | Requirement | Rationale |
|--------|-------------|-----------|
| F6 | [Future enhancement] | [Why deferred] |

---

## Non-Functional Requirements

### Performance

- [ ] [Page load time < Xs]
- [ ] [API response time < Yms]
- [ ] [Support Z concurrent users]

### Security

- [ ] [Authentication/authorization requirements]
- [ ] [Data encryption requirements]
- [ ] [Privacy compliance (GDPR, HIPAA, etc.)]

### Accessibility

- [ ] [WCAG 2.1 Level AA compliance]
- [ ] [Screen reader support]
- [ ] [Keyboard navigation]

### Usability

- [ ] [Mobile responsive design]
- [ ] [Browser compatibility requirements]
- [ ] [Offline capability if needed]

---

## Success Metrics

**North Star Metric:** [Primary metric that defines feature success]

| Metric | Baseline | Target | Measurement Method |
|--------|----------|--------|-------------------|
| [Primary metric] | [Current value] | [Goal value] | [How we measure] |
| [Secondary metric 1] | [Current value] | [Goal value] | [How we measure] |
| [Secondary metric 2] | [Current value] | [Goal value] | [How we measure] |

**Success Definition:** We'll consider this feature successful when [specific criteria].

---

## Out of Scope

[What we're explicitly NOT doing in this version - critical for maintaining focus]

- **[Feature/capability we're deferring]:** [Why deferred, when we might revisit]
- **[Feature/capability we're deferring]:** [Why deferred, when we might revisit]
- **[Feature/capability we're deferring]:** [Why deferred, when we might revisit]

---

## Assumptions

1. [Assumption about users]
2. [Assumption about technical capabilities]
3. [Assumption about business constraints]
4. [Assumption about resources]

---

## Dependencies

### Feature Dependencies

- **Depends on:** [Other feature that must be built first]
- **Blocks:** [Other feature that depends on this]

### Technical Dependencies

- [External API or service]
- [Infrastructure requirement]
- [Third-party integration]

### Cross-Functional Dependencies

- **Design:** [Design work needed]
- **Engineering:** [Technical work needed]
- **Legal/Compliance:** [Legal review needed]
- **Marketing:** [Go-to-market coordination needed]

---

## Open Questions

- [ ] **Q1:** [Question that needs answering]
  - **Impact:** [How this affects scope/timeline]
  - **Owner:** [Who should answer this]
  - **Deadline:** [When we need the answer]

- [ ] **Q2:** [Question that needs answering]
  - **Impact:** [How this affects scope/timeline]
  - **Owner:** [Who should answer this]
  - **Deadline:** [When we need the answer]

---

## Related Documentation

**Validation:** [Link to decisions/YYYY-MM-DD-[feature]-validation.md if exists]

**Research:** [Link to research/YYYY-MM-DD-[topic]-[method].md if exists]

**Product Decisions:**

- [Link to decisions/YYYY-MM-DD-[feature]-[decision].md]
- [Link to decisions/YYYY-MM-DD-[feature]-[decision].md]

**Design Artifacts:**

- **Wireframes:** [Link to design/wireframes/[feature].md if exists]
- **Screen Specs:** [Link to design/screens/[feature].[screen].md if exists]

**Technical Documentation:**

- **ADRs:** [Link to technical/adr/ADR.[topic].md if exists]
- **API Spec:** [Link to technical API documentation if exists]

---

## Revision History

| Date | Version | Changes | Author |
|------|---------|---------|--------|
| YYYY-MM-DD | 1.0 | Initial draft | [Name] |
| YYYY-MM-DD | 1.1 | [Updated section] | [Name] |

---

## Instructions for Using This Template

1. **Fill in YAML frontmatter** - Enables discovery via Grep
2. **Write TL;DR first** - Forces clarity on problem/solution/success
3. **Link to validation/research** - Requirements should be evidence-based
4. **Be specific in requirements** - "User can log in" → "User can log in via email magic link within 30 seconds"
5. **Use tables for scanability** - Easier for LLMs to parse than prose
6. **Define success upfront** - Metrics before building, not after
7. **Be explicit about scope** - "Out of Scope" prevents feature creep
8. **Link bidirectionally** - If you reference a decision, update that decision to reference this requirement
9. **Delete this section** when creating actual requirements