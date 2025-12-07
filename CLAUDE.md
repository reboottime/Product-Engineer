# [Project Name] - AI Agent Context

## Project Overview

[1-2 sentences: What this project does to solve problem for who, and what makes it unique]

**Current Phase:** Customer Discovery

**North Star:** [One sentence - the ultimate measure of success]
<!-- Example: "10k weekly active users converting at 5%" or "Process 1M events/day at <100ms p99" -->

## How to Work With Human

**Communication:**

- Concise: 2-3 sentences max
- No preambles: Just do it, don't announce
- Plans: Bullet points only, no rationale unless the human explicitly ask why and intent learn something

**Collaboration:**

- Use TodoWrite for progress tracking
- Ask questions via AskUserQuestion
- Write multi-line code/content to files (use Edit/Write tools), not terminal echo/cat
- Keep terminal updates to 1-2 sentences

**Artifacts:**

- Simple, direct rationale only (what, why(or why not) in 2-3 bullets each)
- No comprehensive analysis or verbose explanations

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
      learning/            # Tutorials and guides
      manuals/             # How-to documentation
      tasks/               # Action items for humans
   CLAUDE.md               # This file - universal AI agent context
   README.md               # Project readme for humans
```

## Creating Content for Humans

See `/docs/for-human.md` for detailed rules on creating learning materials, manuals, and task files.

## Specialized Agent Context

**Product Agents:** Strategy (`/docs/product/strategy.md`), Requirements (`/docs/product/requirements/`), Design (`/docs/product/design/`)

**Engineering Agents:** Conventions (`/docs/technical/git-conventions.md`), Architecture (`/docs/technical/architecture.md`), API (`/docs/technical/api/`)

**Release Agents:** Git Workflow (`/docs/technical/git-conventions.md`), Deployment (`/docs/technical/deployment.md`)

## Custom Agents

- **[agent-name]**: [One sentence - what this agent does]
