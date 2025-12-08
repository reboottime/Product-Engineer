---
description: Create customer discovery interview guide with questions and probing techniques
argument-hint: [topic]
tags: [product, discovery, pm, customer, research]
---

# Generate Discovery Questions

Use the Task tool to invoke the founding-product-manager agent to create a hypothesis-driven interview guide for customer discovery.

`subagent_type: founding-product-manager`

**Prompt**: "Create customer discovery interview guide for '$ARGUMENTS'.

**Context first:**

- Read `/docs/product/strategy.md` → understand problem space, target audience
- Read `/docs/product/requirements/` → check existing validated insights
- Read `/docs/product/research/insights/` (if exists) → avoid duplicate questions

**Read guidelines first:**

Read `/docs/product/research/discovery-question-guidelines.md` - comprehensive guidelines on creating questions that uncover real customer needs.

**Create interview guide following The Mom Test + JTBD principles:**

1. **Problem validation** - Specific past experiences (not opinions about future)
2. **Commitment evidence** - What they've already done (proves pain is real)
3. **Context** - Their world, tools, workflow, decision-making
4. **Jobs-to-be-Done** - Outcomes they seek (not features they want)
5. **Switching costs** - What keeps them stuck (barriers to adoption)
6. **Prioritization** - Evidence-based ranking (frequency × impact)

**Quality checklist before outputting:**

- [ ] All questions about past, not future
- [ ] At least 3 questions asking for specific stories
- [ ] No hypotheticals ("would you...?")
- [ ] No leading questions mentioning our solution
- [ ] Includes commitment evidence questions
- [ ] Can kill or pivot based on answers

**Write to:** `/docs/product/research/interviews/$ARGUMENTS-guide.md`

**Format:**

```markdown
# Customer Discovery: [Topic]

**Hypothesis:** [What we're trying to validate - be specific]
**Target segment:** [Who to interview - narrow and specific]
**Success criteria:** [What evidence would validate/invalidate hypothesis]

## 1. Problem Validation (Specific Past Experiences)
**Goal:** Get 3+ specific stories about real occurrences

- [Question about last time problem happened]
  - Follow-up: "What did you do?"
  - Follow-up: "How long did that take?"
  - Follow-up: "What was the cost/impact?"

- [Question about workflow walkthrough yesterday/last week]
  - Follow-up: "What else?"
  - Follow-up: "Why did you do it that way?"

[3-5 more questions anchored in specific past events]

## 2. Commitment Evidence (What They've Already Done)
**Goal:** Find proof they've invested time/money/effort

- "What have you already tried to solve this problem?"
- "Have you paid for any solutions? Which ones and how much?"
- "What workarounds have you built yourself?"
- "Who have you talked to about this problem?"
- "What research have you done to find solutions?"

## 3. Context Questions (Understand Their World)

- [Role and responsibilities]
- [Decision-making authority and budget access]
- [Current tools and workflow]
- [Team structure and who else is affected]
- [Buying process if B2B]

## 4. Jobs-to-be-Done (Outcomes, Not Features)

- "What are you trying to accomplish when [problem occurs]?"
- "How do you measure success on this?"
- "What would 'done' look like?"
- "What would solving this enable you to do next?"
- "How do you want to feel when this is solved?"

## 5. Switching Costs (Barriers to Change)

- "What keeps you using [current solution] despite the problems?"
- "What would you have to change or give up to switch?"
- "Who else would be affected if you changed approaches?"
- "When was the last time you switched tools? How did it go?"
- "What's the risk of trying something new?"

## 6. Prioritization (Evidence-Based)

- "Which problem happened most often this week/month?" (frequency)
- "Which problem costs you the most time/money/opportunity?" (impact)
- "If you had a magic wand, what would you solve first?"
- "What problem are you actively trying to solve right now?"
- "Can we follow up in [timeframe] to see how [current approach] worked?"

## Interview Tips for [Topic]
- [Specific tips based on topic]
- Watch for: [Red flags or validation signals]
- Good follow-ups: [Context-specific probing questions]

## Quality Checklist
- [ ] All questions anchored in past, not future
- [ ] At least 3 questions asking for specific stories
- [ ] No hypotheticals ("would you...?")
- [ ] No leading questions mentioning our solution
- [ ] Includes commitment evidence questions
- [ ] Can kill or pivot based on answers
```"
