# Founding Product Manager - Quick Reference

## Quick Start

**Agent invocation:**

```
@agent-founding-product-manager [your instruction]
```

**Examples:**

- `generate discovery questions for [topic]`
- `create user profile for [segment]`
- `validate this feature idea`

**Slash commands by workflow:**

| Phase | Command | Purpose |
|-------|---------|---------|
| **Setup** | `/pm.define-project-context` | Set up product sections in CLAUDE.md |
| **Discovery** | `/pm.generate-discovery-questions [topic]` | Create interview guide |
| | `/pm.create-user-profile [segment]` | User profile from insights |
| | `/pm.process-customer-research [file]` | Synthesize interview insights |
| | `/pm.analyze-competitors [topic]` | Competitive landscape analysis |
| **Planning** | `/pm.validate-feature [feature-name]` | RICE scoring, build now/later/never |
| | `/pm.write-prd [feature-name]` | Detailed PRD for validated feature |
| | `/pm.plan-roadmap` | Now/Next/Later roadmap |
| **Collaboration** | `/pm.propose-feature [idea]` | PM + design lead evaluation |
| | `/pm.doc-decision` | Document product decision |
| **Post-Launch** | `/pm.review-feature [feature-name]` | 2-4 week post-launch review |
| | `/pm.sync-features [file-path]` | Sync implementation to docs |
| **Maintenance** | `/pm.review-project-context` | Quarterly strategy review |
| **Transition** | `/pm.handoff-to-growth` | Prepare handoff to growth PM |

**Use for:** 0→1 discovery through POC. Validates problems, kills bad ideas fast, documents learning.

**Won't do:** Growth optimization, A/B testing, scaling strategy (hands off at PMF)

## What It Needs

- Project phase from `CLAUDE.md` (Discovery/POC only)
- Product strategy from `/docs/product/strategy.md`
- Customer insights (creates if missing)

## What You Get

| Command | Output Location | Contents |
|---------|----------------|----------|
| `define-project-context` | `/CLAUDE.md` | Product sections: problem, solution, metrics, phase |
| `generate-discovery-questions` | `/docs/product/research/interviews/[topic]-guide.md` | Mom Test questions, probing follow-ups, success criteria |
| `create-user-profile` | `/docs/product/research/insights/user-profile-[segment].md` | Demographics, psychographics, JTBD, switching costs |
| `process-customer-research` | `/docs/product/research/insights/[theme].md` | Synthesized patterns across interviews |
| `analyze-competitors` | `/docs/product/competitive/[topic]-analysis.md` | Market gaps, differentiation strategy |
| `validate-feature` | Terminal output | RICE score, build now/later/never decision |
| `write-prd` | `/docs/product/requirements/[feature].md` + index | Detailed PRD, updated requirements index |
| `plan-roadmap` | `/docs/product/strategy.md` | Now/Next/Later roadmap with scoring |
| `propose-feature` | Various (PRD/design/task) | Collaborative PM+design evaluation |
| `doc-decision` | `/docs/product/decisions/[yyyy-mm-dd].[topic].md` + index | Decision rationale, updated decision catalog |
| `review-feature` | `/docs/product/post-mortems/[feature]-review.md` | Metrics analysis, iterate/pivot/sunset |
| `sync-features` | Updates PRDs + design specs | Syncs implementation changes to docs |
| `review-project-context` | `/CLAUDE.md` | Updated strategy, phase validation |
| `handoff-to-growth` | `/docs/product/handoff-brief.md` + validated insights | Complete handoff package for growth PM |

## Research Folder Structure

```
/docs/product/research/
├── interviews/          # Raw conversations (YYYY-MM-DD-[name].md)
├── insights/            # Patterns across 3+ interviews ([theme].md)
├── learnings/           # Experiment results ([feature]-experiment.md)
└── validated/           # Proven hypotheses for handoff
```

**Create new file when:**

- Each interview (one conversation = one file)
- Pattern emerges (3+ people say same thing)
- Experiment starts/completes

**Update existing when:**

- Adding evidence to pattern
- Experiment data comes in
- Refining validated hypothesis

## Agent Challenges You On

| Situation | Agent Response | Why |
|-----------|---------------|-----|
| Feature without evidence | "What problem? What evidence?" | Forces validation before build |
| Solution before problem | "What are we learning? Validated need?" | Prevents solution-first trap |
| Assumptions as facts | "What data? Can we test first?" | Exposes bias risk |
| Building before learning | "Can we learn without building?" | Optimizes for learning speed |

**Agent trusts you on:** Engineering implementation, technical feasibility, architecture

**Agent recommends (you decide):** Prioritization, kill/continue/pivot, research methodology

**Agent consults:** Business model pivots, target audience shifts, resource tradeoffs

## Common Workflows

### Initial Setup (New Project)

```
/pm.define-project-context → Human collaborates → CLAUDE.md populated
```

### Discovery Phase (Validate Problem)

| Step | Action | Output |
|------|--------|--------|
| 1 | Human proposes idea | - |
| 2 | `/pm.generate-discovery-questions [topic]` | Interview guide |
| 3 | Human conducts 5+ interviews | Raw notes per conversation |
| 4 | `/pm.process-customer-research` | Synthesized insights |
| 5 | `/pm.analyze-competitors [topic]` (optional) | Competitive analysis |
| 6 | `/pm.create-user-profile [segment]` (optional) | Detailed user profile |

### POC Phase (Build & Validate)

| Step | Action | Output |
|------|--------|--------|
| 1 | Human suggests feature | - |
| 2 | `/pm.propose-feature [idea]` | PM + design collaborative evaluation |
| 3 | If approved: `/pm.write-prd [feature]` | Detailed PRD + updated index |
| 4 | Human builds MVP | - |
| 5 | After 2-4 weeks: `/pm.review-feature [feature]` | Metrics review, iterate/pivot/sunset |
| 6 | If code changes made: `/pm.sync-features` | Docs synced with implementation |

### Decision Making

```
Option 1: /pm.propose-feature [idea] → PM + design evaluate → Auto-documents if approved
Option 2: /pm.doc-decision → Human + PM document decision manually
```

### Prioritization Scenarios

| Scenario | Agent Action | Reasoning |
|----------|--------------|-----------|
| Feature requested by 3/15 users | Recommend deprioritize | 20% mention rate, not validated |
| Feature requested by 12/15 users | Recommend prioritize | 80% mention rate, clear pattern |
| No evidence for feature | Challenge with "What problem?" | Prevent building without validation |

### Maintenance & Transition

```
Quarterly: /pm.review-project-context → Strategy review
Roadmap planning: /pm.plan-roadmap → Now/Next/Later
At PMF: /pm.handoff-to-growth → Prepare growth PM handoff
```

## Outputs by Phase

| Phase | Folder | Contents |
|-------|--------|----------|
| **Setup** | `/CLAUDE.md` | Product context, problem, solution, metrics |
| | `/docs/product/strategy.md` | North star, target users, roadmap |
| **Discovery** | `/research/interviews/` | Raw conversations (YYYY-MM-DD-[name].md) |
| | `/research/insights/` | Patterns across 3+ interviews |
| | `/competitive/` | Competitor analysis, market gaps |
| **POC** | `/requirements/[feature].md` | PRDs (problem → MVP → metrics) |
| | `/metrics/[feature].md` | Leading indicators to track |
| | `/research/learnings/` | Experiment results, continue/pivot/kill |
| | `/decisions/` | Product decisions with rationale |
| **Post-Launch** | `/post-mortems/` | Feature reviews, iteration recommendations |
| **Handoff** | `/research/validated/` | Proven hypotheses |
| | `/handoff-brief.md` | Complete package for growth PM |

## Transition Criteria

**Hand off to growth PM when:**

- Week-2 retention >40%
- User acquisition path exists
- Core value validated
- PMF indicators present

Agent creates `/docs/product/research/validated/handoff-summary.md`

## Common Fixes

| Problem | Solution |
|---------|----------|
| Agent repeats questions | Check `/research/interviews/` exists, has notes |
| No prioritization guidance | Run `/pm.process-customer-research` to synthesize |
| Can't track learning over time | Use folder structure, one file per interview |
| Missing context between conversations | Document insights in `/research/insights/` |

---

**Learning resource:** `/for-human/learning/customer-discovery.interview-techniques.md`

**Template:** `/docs/product/requirements/founding-pm.template.md`
