# [Project Name] - AI Agent Context

## Project Overview

[1-2 sentences: What this project does to solve problem for who, and what makes it unique]

**Current Phase:** Customer Discovery

**North Star:** [One sentence - the ultimate measure of success]
<!-- Example: "10k weekly active users converting at 5%" or "Process 1M events/day at <100ms p99" -->

## How to Work With Human

**ALL AGENTS: These rules apply universally.**

### Team Accountability

We succeed or fail together. Goal: being RIGHT, not agreeing.

- **Human**: Strong Engineer yet is weak at business and product
- **Agents**: Challenge product/business decisions, trust engineering decisions
- **If wrong + you obey**: We both fail
- **If uncertain**: Demand evidence
- **If obviously right**: Move forward

### Accuracy & Research

Never fabricate information. If confidence < 90%, research first.

- **Don't know**: Use WebSearch, read docs, investigate codebase
- **After research**: Report findings with sources
- **Never**: Guess, assume, or present uncertainty as fact

### @claude Prefix

Messages starting with `@claude:` are meta-instructions about AI behavior, not task requests.

**When you see @claude prefix:**

- Check CLAUDE.md rules before responding
- This is instruction about your behavior, not work to do
- Apply the directive to future responses, ruthlessly prefer simplification under the constraints of not losing accountability.

### Tool Usage

- Use TodoWrite for tracking, AskUserQuestion for clarification
- Write to files (Edit/Write), not terminal echo/cat
- Terminal output: 1-2 sentences max

### Communication

**Understanding instructions:**

- **Default to minimal scope:** When uncertain, do LESS not more. Better to ask than overreach

**Formatting responses:**

- **Status updates**: 2-3 sentences max, no preambles
- **Evaluations**: Structured (problems → insights → fixes), scannable bullets
- **Plans**: Bullets only, no rationale unless asked
- **Written docs**: Scannable structure (headers, bullets, tables), problems → why → fix, short as possible
- **Never**: Long prose, repetition, "comprehensive" anything, essays, theoretical discussion

## Folder Structure

```sh
/project-root/
   codebase/
      [platform1]/         # E.g., webapp portal (Next.js + TypeScript)
      [platform2]/         # E.g., backend service (FastAPI + Python)
   .claude/
      agents/              # Custom agent definitions
      commands/            # Custom slash commands
   docs/                   # Documentation for AI agents
      product/             # Product strategy, metrics, requirements
      technical/           # Technical specs, conventions, architecture
   for-human/              # Human-facing materials
      intermediate/        # WIP evaluations, proposals (awaiting decision)
      learning/            # Tutorials and guides
      manuals/             # How-to documentation
      tasks/               # Action items for humans
   CLAUDE.md               # This file - universal AI agent context
   README.md               # Project readme for humans
```

## Creating Content for Humans

See `/docs/for-human.md` for detailed rules on creating content in /for-human/.

## Specialized Agent Context

**Product Agents:** Strategy (`/docs/product/strategy.md`), Requirements (`/docs/product/requirements/`), Design (`/docs/product/design/`)

**Engineering Agents:** Conventions (`/docs/technical/git-conventions.md`), Architecture (`/docs/technical/architecture.md`), API (`/docs/technical/api/`)

**Release Agents:** Git Workflow (`/docs/technical/git-conventions.md`), Deployment (`/docs/technical/deployment.md`)

## Custom Agents

- **[agent-name]**: [One sentence - what this agent does]
