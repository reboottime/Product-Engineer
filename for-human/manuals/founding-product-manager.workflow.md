# Founding Product Manager - Workflow Guide

## What This Agent Does

Validates problems and designs MVPs for 0→1 products. Optimizes for learning speed over process. Kills bad ideas fast, doubles down on winners.

## When It Runs

**Discovery through POC phases** (0→1 only). Hands off to growth PM when you find product-market fit.

## Available Commands

Use these slash commands to work with the founding PM agent:

- **`/pm.generate-discovery-questions [topic]`** - Creates interview guide following The Mom Test + JTBD principles
  - Reads: strategy, existing insights
  - Outputs: `/docs/product/research/interviews/[topic]-guide.md`
  - Guidelines: `/docs/product/research/discovery-question-guidelines.md`

- **`/pm.create-user-profile [segment]`** - Creates end user profile following Disciplined Entrepreneur methodology
  - Reads: strategy, interviews, insights
  - Outputs: `/docs/product/research/insights/user-profile-[segment].md`
  - Includes: demographics, psychographics, day-in-the-life, JTBD, switching costs

**For learning:** See `/for-human/learning/customer-discovery.interview-techniques.md` for how to conduct effective interviews.

## Input → Process → Output

### Takes In

- Project overview from `CLAUDE.md` (current phase, north star)
- Product strategy from `/docs/product/strategy.md` (problem, target users)
- Customer insights (creates if missing)

### Process

1. **Validate problem** - Interview customers, document pain points
2. **Design solution** - Define MVP scope, success metrics
3. **Prioritize ruthlessly** - RICE scoring, kill low-confidence bets
4. **Track learning** - Document what worked/failed
5. **Iterate or kill** - Data-driven continue/pivot/stop decisions

### Outputs

**Artifacts organized by learning type:**

```sh
/docs/product/research/
├── interviews/          Raw customer conversations
├── insights/            Patterns across interviews
├── learnings/           What worked/failed in experiments
└── validated/           Proven hypotheses for handoff

/docs/product/requirements/
├── founding-pm.template.md  Template for lean requirements
└── [feature].md              Lean requirements (problem → MVP → validation)

/docs/product/metrics/
└── [feature].md         Leading indicators to track
```

## The Folder System (Q&A)

### Why separate folders instead of one research file?

**Learning accumulates over time.** 0→1 means:

- Week 1: 5 interviews
- Week 3: 12 more interviews + POC results
- Week 6: 8 validation conversations

Single file = 2000 lines, impossible to scan. Folders = organized by learning type.

### What goes in each folder?

**interviews/** - Raw notes from customer conversations

- Format: `YYYY-MM-DD-[participant-name].md`
- What you heard, direct quotes, follow-up questions
- One file per conversation

**insights/** - Synthesized patterns

- Format: `[theme].md` (e.g., `context-switching-pain.md`)
- Pattern across 3+ interviews
- Quotes supporting the pattern

**learnings/** - Experiment results

- Format: `[feature]-experiment.md`
- What you built, hypothesis, results
- Decision: continue/pivot/kill

**validated/** - Proven hypotheses ready for scale

- Format: `[hypothesis].md`
- Evidence that validates this works
- Handoff artifact to growth PM

### When do I create vs. update files?

**Create new:**

- Each interview (new conversation = new file)
- New pattern emerges (3+ people say same thing)
- New experiment starts

**Update existing:**

- Add supporting evidence to pattern
- Update experiment results as data comes in
- Refine validated hypothesis

### How does the agent use these?

**Before building:** Checks insights/ for validated pain points
**During prioritization:** Counts evidence (5 interviews > 1 interview)
**After shipping:** Writes to learnings/ what happened
**At handoff:** Packages validated/ for growth PM

**Note:** Agent references `interviews/` and `insights/` folders in config. The `learnings/` and `validated/` folders are recommended structures for organizing experiments and handoff artifacts - create them as needed during the workflow.

### What if I skip this structure?

Agent loses context between conversations. Without persistent learning:

- Repeats questions already answered
- Forgets why features were killed
- Can't prioritize by evidence strength
- No handoff artifact for next phase

## Collaboration Model

**Hypothesis-driven, evidence-based:**

```
Human proposes idea → Agent asks "What evidence?" → Validate before build
```

**Agent challenges you when:**

- **Feature without evidence** → "What problem? What evidence? [explains risk]"
- **Solution before problem** → "What are we learning? Validated need? [explains trap]"
- **Assumptions as facts** → "What data? Can we test first? [explains bias risk]"
- **Building before learning** → "Can we learn without building? [explains tradeoff]"

Agent explains WHY it's challenging, not just what's wrong.

**Agent trusts you on:**

- Engineering implementation decisions
- Technical feasibility and approach
- React/architecture choices

**Agent recommends (you decide):**

- What to build next → "Prioritize X because [reasoning]. Your call?"
- What NOT to build → "Cut Y because [no evidence]. Agree?"
- Research methodology → "Try [approach] because [goal]. Sound right?"
- Kill/continue/pivot → "Kill based on [data]. Thoughts?"

**Agent consults (AskUserQuestion):**

- Business model pivots
- Target audience shifts
- Technical feasibility questions
- Resource/timeline tradeoffs

## Example Flow: Discovery Phase

1. **Human:** "I want to build a task manager for ADHD users"

2. **Human runs:** `/pm.generate-discovery-questions adhd-task-management`

3. **Agent creates:** `/docs/product/research/interviews/adhd-task-management-guide.md`
   - Questions to validate pain (following The Mom Test principles)
   - Interview script with probing follow-ups
   - Success criteria (10+ conversations confirming urgent pain)

4. **Human conducts interviews** using the guide (reference: `/for-human/learning/customer-discovery.interview-techniques.md`)

5. **Agent writes:** `/docs/product/research/interviews/YYYY-MM-DD-[name].md` for each

6. **After 5 interviews, agent writes:** `/docs/product/research/insights/task-visibility-problem.md`
   - Pattern: "Task lists invisible in fullscreen = forgetting what to work on"
   - Evidence: 5/5 mentioned this, quotes included

7. **Optional - Human runs:** `/pm.create-user-profile adhd-knowledge-workers`
   - Creates detailed user profile from interview insights
   - Demographics, psychographics, day-in-the-life, JTBD

8. **Agent writes:** `/docs/product/requirements/visible-task-overlay.md`
   - Problem: Task lists invisible in fullscreen
   - MVP: Always-visible overlay in Chrome
   - Success metric: Users reference tasks 5+ times/day
   - Out of scope: Mobile, integrations, AI suggestions

9. **Human builds MVP**

10. **Agent tracks:** `/docs/product/metrics/visible-task-overlay.md`
    - Activation: Extension enabled
    - Core action: Tasks referenced during work
    - Leading indicator: Daily active usage

11. **After 2 weeks, agent writes:** `/docs/product/research/learnings/visible-task-overlay-experiment.md`
    - Hypothesis: Visibility prevents context-switching
    - Results: 4/5 users reference tasks 8+ times/day
    - Decision: **Validated** - continue building

12. **Agent updates:** `/docs/product/research/validated/task-visibility-solves-adhd-focus.md`
    - For handoff to growth PM when scaling

## Example Flow: POC Phase

1. **Human:** "Users requested calendar integration"

2. **Agent asks:** "How many users requested this? What problem does it solve?"

3. **Human:** "3 users mentioned it"

4. **Agent checks:** `/docs/product/research/interviews/` - finds 15 total conversations
   - 3/15 = 20% mention rate
   - Not a pattern yet

5. **Agent recommends:** "Prioritize below. Current MVP (task visibility) validated by 12/15 users. Focus on scaling that first."

6. **Decision:** Kill calendar integration idea (for now)

7. **Agent documents:** Brief note in `/docs/product/research/learnings/calendar-integration-deprioritized.md`

## What Makes This Different

**Learning-optimized, not shipping-optimized:**

- Documents WHY features were killed (prevents repeating mistakes)
- Counts evidence strength (5 interviews > 1 interview)
- Challenges assumptions (demand proof before build)

**Handoff-ready:**

- `/validated/` folder = everything proven, ready to scale
- Growth PM reads this and knows what works

**Ruthless prioritization:**

- Default answer: "No"
- Builds only what validates hypothesis
- Kills features that don't prove value

## Output Locations

**Research artifacts:** `/docs/product/research/[type]/[file].md`
**Requirements:** `/docs/product/requirements/[feature].md`
**Metrics:** `/docs/product/metrics/[feature].md`

Growth PM reads `/validated/` when taking over.

## Transition Criteria

**Hand off to growth PM when:**

- Week-2 retention >40%
- Clear user acquisition path exists
- Core value proposition proven
- Product-market fit indicators present

Agent creates `/docs/product/research/validated/handoff-summary.md` with everything learned.
