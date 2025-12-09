# Agentic System Roadmap

**Purpose:** Strategic roadmap for building your agentic system on Claude Code.

## Vision

Architect an agentic system to run product building & selling (0-1, 1-10 phases) on Claude Code, demonstrating a systematic method to ship fast and effectively.

## Design Constraints

- **Claude Code limits:** No customer interviews, no Figma, token limits
- **LLM limits:** Hallucination, no infinite memory, needs structured prompts
- **Solo founder context:** Human provides insights, agents automate execution

## Phases

### Phase 1: Foundation (0-1 MVP)

**Goal:** System works within constraints - human provides insights, agents automate execution

**Team Design** (define agent roles & interactions)

- Map 0-1 workflow to minimal agent set
- Define each agent's scope (avoid overlap → token efficiency)
- Design handoff protocols (who calls who, when)
- Document in `/for-human/manuals/agentic-system-team.md`

**Memory System** (overcome token limits)

- Optimize docs/ structure for agent context efficiency
- Create templates that compress knowledge (PRD, spec, wireframe)
- Implement /sys.optimize-doc for ongoing compression

**Core Agents** (minimal viable set)

- PM: Decision frameworks (RICE, validation), not decisions themselves
- PM: Synthesize human-provided customer insights into docs
- PM: Generate PRDs from validated problems
- Design Lead: Markdown wireframes (not Figma)
- Design Lead: Behavior-focused specs (not visual design)
- Release Manager: Feature-based git workflow
- Release Manager: Auto-generate commit messages & PRs

**Human-Agent Interface** (how human guides within LLM limits)

- Slash commands for repeatable workflows
- AskUserQuestion for validation gates
- Clear handoff points (human does discovery → agent structures)

### Phase 2: Optimization (Make it Efficient)

**Goal:** System operates within token budget, agents collaborate effectively

**Token Efficiency**

- Measure context usage per workflow
- Compress agent prompts
- Smart context loading (only what's needed)

**Agent Collaboration**

- PM ↔ Design Lead handoff protocol
- Design Lead ↔ Code agents handoff
- Shared context management

**Validation Workflows**

- Human validates before each major phase
- Metrics to track decision quality
- Feedback loops to improve prompts

### Phase 3: Validation (Test via Toy App)

**Goal:** Prove system works end-to-end within constraints

**Discovery → Design → Build**

- Human: Do customer interviews, provide insights
- Agent: Synthesize into problem/solution docs
- Agent: Generate PRD, wireframes, specs
- Agent: Implement code
- Agent: Ship via git workflow

**Measure Effectiveness**

- Time saved vs manual approach
- Decision quality (did PM frameworks help?)
- Code quality (does it work?)

### Phase 4: Scale to 1-10 (Future)

**Goal:** Extend beyond MVP to growth phase

**Growth Capabilities**

- Marketing agent (landing pages, messaging)
- Analytics interpretation (human provides data)
- Iteration workflows (A/B test setup)

**Advanced Features**

- Multi-platform coordination
- Technical debt management
- Scale-focused architecture decisions

## Success Criteria

**Phase 1 Done When:**

- Team design documented & validated
- 3 core agents operational (PM, Design, Release)
- Memory system reduces context usage by 50%
- Human can use slash commands for common workflows

**Phase 3 Done When:**

- Built & shipped a toy app using only the agentic system
- Documented time saved vs manual approach
- Identified gaps & improvements

**System Ready When:**

- Can go from problem → shipped code in <3 days for simple features
- Agents handle 80% of execution, human provides 20% insights
- Token usage stays under limits for typical workflows
