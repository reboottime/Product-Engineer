---
description: Create end user profile following Disciplined Entrepreneur methodology
argument-hint: [segment-name]
tags: [product, discovery, pm, customer, research, user-profile]
---

# Create End User Profile

Use the Task tool to invoke the founding-product-manager agent to create a detailed end user profile following Disciplined Entrepreneur principles.

`subagent_type: founding-product-manager`

**Prompt**: "Create end user profile for '$ARGUMENTS' segment following Disciplined Entrepreneur methodology.

**Context first:**

- Read `/docs/product/strategy.md` → understand target market, problem space
- Read `/docs/product/research/interviews/` → existing customer conversations
- Read `/docs/product/research/insights/` → validated patterns
- Check for existing user profiles to avoid duplication

**Create comprehensive end user profile:**

## 1. Profile Overview

- Segment name and description
- Why this is the beachhead market
- Estimated market size (TAM/SAM/SOM if known)

## 2. Demographics

- Age range
- Gender (if relevant)
- Education level
- Income/budget range
- Geographic location
- Job title/role
- Company size (if B2B)
- Industry (if B2B)

## 3. Psychographics

- Values and beliefs
- Attitudes toward technology/change
- Lifestyle characteristics
- Goals and aspirations
- Fears and frustrations
- Information sources (where they learn)

## 4. Day-in-the-Life

- Typical daily workflow
- Key tasks and responsibilities
- Tools and systems used
- Pain points throughout the day
- When the problem surfaces
- Impact on their success

## 5. Decision-Making Profile

- Decision criteria (what matters most)
- Buying authority (can they purchase?)
- Budget access and approval process
- Risk tolerance
- Time to decision
- Influencers and stakeholders

## 6. Problem Context

- Primary pain points (ranked)
- Current solutions/workarounds
- Why current solutions fail
- Urgency of problem (nice-to-have vs. critical)
- Frequency of problem occurrence
- Cost of not solving (time/money/opportunity)

## 7. Jobs-to-be-Done

- Functional jobs (tasks to complete)
- Emotional jobs (how they want to feel)
- Social jobs (how they want to be perceived)
- Success metrics (how they measure progress)

## 8. Behavioral Characteristics

- Tech savviness level
- Adoption pattern (early adopter vs. late majority)
- Preferred communication channels
- Purchase behavior and triggers
- Onboarding expectations

## 9. Evidence Base

- Number of interviews supporting this profile
- Key quotes from customers
- Data sources used
- Confidence level (high/medium/low)
- What still needs validation

**Principles:**

- Evidence-based: Every claim backed by interview data or research
- Specific: "Sarah, 32, product manager at 50-person SaaS startup" not "professionals"
- Behavioral: Focus on what they do, not just demographics
- Jobs-focused: Frame around outcomes they seek, not features they want
- Beachhead-ready: Narrow enough to target, large enough to matter

**Write to:** `/docs/product/research/insights/user-profile-$ARGUMENTS.md`

**Format:**

```markdown
# End User Profile: [Segment Name]

**Last Updated:** YYYY-MM-DD
**Confidence Level:** [High/Medium/Low]
**Evidence Base:** [X interviews, Y data sources]

## Profile Overview
[Segment description and beachhead rationale]

## Demographics
[Structured demographic data]

## Psychographics
[Values, attitudes, lifestyle]

## Day-in-the-Life
[Narrative describing typical day and when problem surfaces]

## Decision-Making Profile
[How they buy, who influences, what criteria matter]

## Problem Context
1. **[Pain Point 1]** - [Description, frequency, impact]
2. **[Pain Point 2]** - [Description, frequency, impact]
3. **[Pain Point 3]** - [Description, frequency, impact]

Current solutions: [What they use now]
Why it fails: [Gap our product fills]

## Jobs-to-be-Done
**Functional:** [Tasks to complete]
**Emotional:** [How they want to feel]
**Social:** [How they want to be perceived]

## Behavioral Characteristics
- Tech savviness: [Level]
- Adoption pattern: [Early adopter/Early majority/etc.]
- Preferred channels: [Where to reach them]
- Purchase triggers: [What drives decision]

## Evidence & Validation
**Supporting evidence:**
- [Interview finding 1 with quote]
- [Interview finding 2 with quote]
- [Data point from research]

**Still needs validation:**
- [Assumption 1 to test]
- [Assumption 2 to test]

## Example Persona
**Name:** [First name for reference]
**Quote:** "[One sentence capturing their main frustration]"

[2-3 paragraph narrative bringing this person to life - their day, their problem, their desired outcome]
```

**After creation:**

- Use this profile to inform prioritization decisions
- Reference when writing requirements (who is this for?)
- Update as you learn more from interviews
- Create interview guide to validate assumptions if confidence is low"
