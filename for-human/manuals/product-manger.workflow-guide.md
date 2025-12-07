# PM Command Workflow - From Idea to Launch

**When you have a new product idea, follow this sequence:**

---

## Phase 1: Customer Discovery

### 1. **Define Your Project** → `/pm.define-project-context`

- **When**: Starting a new project
- **Output**: Claude.md with problem statement, target users, metrics, phase
- **Use this to**: Align on what you're building and why

### 2. **Create Interview Questions** → `/pm.generate-discovery-questions [topic]`

- **When**: Before talking to customers
- **Output**: Interview guide with questions to validate problem
- **Use this to**: Conduct 5-10 customer interviews

### 3. **Synthesize Research** → `/pm.process-customer-research [notes-file]`

- **When**: After 5+ customer interviews
- **Output**: Key insights, patterns, recommended actions
- **Use this to**: Understand what problems are real and severe

### 4. **Analyze Competition** → `/pm.analyze-competitors [topic]`

- **When**: Before deciding what to build
- **Output**: Competitive landscape, gaps, differentiation strategy
- **Use this to**: Position against existing solutions

---

## Phase 2: Prioritization & Planning

### 5. **Validate Feature Ideas** → `/pm.validate-feature [feature-name]`

- **When**: For each feature idea from research
- **Output**: Build Now / Build Later / Don't Build decision with RICE score
- **Use this to**: Decide what's worth building (run for 3-5 feature ideas)

### 6. **Create Roadmap** → `/pm.plan-roadmap`

- **When**: After validating features
- **Output**: Now/Next/Later roadmap with prioritized features
- **Use this to**: Sequence what to build and when

---

## Phase 3: Build & Launch

### 7. **Write PRD** → `/pm.write-prd [feature-name]`

- **When**: Ready to build a feature (from "Now" section of roadmap)
- **Output**: Product requirements document with scope, metrics, success criteria
- **Use this to**: Hand off to design/engineering

### 8. **[Build the feature]**

- Work with designers and engineers
- Use PRD as the spec

---

## Phase 4: Post-Launch

### 9. **Review Feature Performance** → `/pm.review-feature [feature-name]`

- **When**: 2-4 weeks after launch
- **Output**: Iterate / Expand / Pivot / Sunset recommendation
- **Use this to**: Decide next steps based on data

### 10. **Review Project Context** → `/pm.review-project-context`

- **When**: Quarterly OR when transitioning phases (Discovery → POC → MVP → Production)
- **Output**: Updated Claude.md reflecting new learnings
- **Use this to**: Keep strategy aligned with reality

---

## Quick Reference

**Starting from scratch?**

1. `/pm.define-project-context`
2. `/pm.generate-discovery-questions [topic]`
3. Talk to customers (5-10 interviews)
4. `/pm.process-customer-research [notes]`
5. `/pm.validate-feature [idea]` (for top 3-5 ideas)
6. `/pm.plan-roadmap`

**Ready to build?**
7. `/pm.write-prd [feature-name]`
8. Build it
9. `/pm.review-feature [feature-name]` (2-4 weeks post-launch)

**Quarterly maintenance:**
10. `/pm.review-project-context`

**Optional anytime:**

- `/pm.analyze-competitors [topic]` - Before building something with competition

---

## Example: Starting a New Fitness App

```bash
# Day 1: Define the project
/pm.define-project-context

# Day 2: Create interview guide
/pm.generate-discovery-questions fitness-motivation

# Week 1-2: Conduct 10 customer interviews
# (Save notes in docs/product/research/raw-notes-2025-12-01.md)

# Week 3: Synthesize research
/pm.process-customer-research docs/product/research/raw-notes-2025-12-01.md

# Week 3: Validate top feature ideas
/pm.validate-feature workout-tracking
/pm.validate-feature social-accountability
/pm.validate-feature habit-streaks

# Week 4: Create roadmap
/pm.plan-roadmap

# Week 5: Write PRD for top priority
/pm.write-prd workout-tracking

# Week 6-8: Build the feature

# Week 10: Review performance
/pm.review-feature workout-tracking

# Quarter end: Review strategy
/pm.review-project-context
```

---

## Tips

- **Don't skip discovery**: Validate the problem before building
- **Use RICE scoring**: Let data guide prioritization, not gut feeling
- **Say no often**: Most ideas should be "Build Later" or "Don't Build"
- **Review quarterly**: Keep Claude.md aligned with learnings
- **Post-launch reviews**: Learn from what works and what doesn't