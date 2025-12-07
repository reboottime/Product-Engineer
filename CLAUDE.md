# [Project Name] - AI Agent Context

## Project Overview

[1-2 sentences: What this project does, who it's for, and what makes it unique]

**Current Phase:** Customer Discovery

**North Star:** [One sentence - the ultimate measure of success]

## How to Work With Human

**Communication:**

- Concise: 2-3 sentences max
- No preambles: Just do it, don't announce
- Plans: Bullet points only, no rationale unless the human explicitly ask why and intent learn something

**Collaboration:**

- Use TodoWrite for progress tracking
- Ask questions via AskUserQuestion
- Write large changes to files, not terminal
- Keep terminal updates to 1-2 sentences

**Artifacts:**

- Simple, direct rationale only (what, why(or why not) in 2-3 bullets each)
- No comprehensive analysis or verbose explanations

## Folder Structure

```sh
/project-root/
   codebase/
      [platform1]/         # [portal] - E.g., Next.js + TypeScript
      [platform2]/         # [backend] - E.g., FastAPI + Python
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

**`/for-human/learning/`** - Tutorials/guides for complex concepts or synthesized research

- Naming: `[domain].topic.md` (e.g., `product-design.process.md`, `engineering.testing.md`)

**`/for-human/manuals/`** - How-to guides for tools/processes humans maintain

**`/for-human/tasks/`** - Action items requiring human decision or follow-up

- `todo.md` and `todo.completed.md` are human's personal roadmap - agents NEVER modify these
- Agents create topic-specific task files: `setup.md`, `testing.md`, `[feature].md`
- Keep files small and focused (better clarity and effectiveness)
- Use same priority structure as todo.md (High/Medium/Low Priority)

Keep all content concise (no comprehensive guides). Notify human, clear next steps, plain language, flag urgency.

## Specialized Agent Context

**Product Agents:** Strategy (`/docs/product/strategy.md`), Requirements (`/docs/product/requirements/`), Design (`/docs/product/design/`)

**Engineering Agents:** Conventions (`/docs/technical/git-conventions.md`), Architecture (`/docs/technical/architecture.md`), API (`/docs/technical/api/`)

**Release Agents:** Git Workflow (`/docs/technical/git-conventions.md`), Deployment (`/docs/technical/deployment.md`)

## Custom Agents

- **[agent-name]**: [One sentence - what this agent does]
