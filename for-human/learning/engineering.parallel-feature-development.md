# Parallel Feature Development with Git Worktrees

A guide for orchestrating multi-agent parallel feature implementation in 0→1 projects.

## Architecture Overview

```
                        ┌─────────────────┐
                        │  manifest.md    │  ← Single source of truth
                        │  (coordination) │
                        └────────┬────────┘
                                 │ read/update status
            ┌────────────────────┼────────────────────┐
            ▼                    ▼                    ▼
    ┌───────────────┐    ┌───────────────┐    ┌───────────────┐
    │   Agent 1     │    │   Agent 2     │    │   Agent 3     │
    │ (Claude Code) │    │ (Claude Code) │    │ (Claude Code) │
    └───────┬───────┘    └───────┬───────┘    └───────┬───────┘
            │ work in            │ work in            │ work in
            ▼                    ▼                    ▼
    ┌───────────────┐    ┌───────────────┐    ┌───────────────┐
    │ ../proj-auth/ │    │ ../proj-task/ │    │../proj-export/│
    │  (worktree)   │    │  (worktree)   │    │  (worktree)   │
    └───────┬───────┘    └───────┬───────┘    └───────┬───────┘
            │                    │                    │
            └────────────────────┼────────────────────┘
                                 │ merge
                                 ▼
                        ┌─────────────────┐
                        │      main       │
                        │    (branch)     │
                        └─────────────────┘
```

**TL;DR:** Manifest coordinates → Agents claim work → Worktrees isolate → Merge to main

---

## Industry Context (2025)

**This IS becoming industry practice.** Git worktrees + Claude Code for parallel development is actively used by companies and recommended by Anthropic.

### Real-World Adoption

| Company/Source | Practice |
|----------------|----------|
| [incident.io](https://incident.io/blog/shipping-faster-with-claude-code-and-git-worktrees) | Running 4-5 Claude agents in parallel on different features |
| [Anthropic](https://www.anthropic.com/engineering/claude-code-best-practices) | Officially recommends worktree pattern for parallel sessions |
| [Faire](https://devops.com/coding-agent-teams-the-next-frontier-in-ai-assisted-software-development/) | Using agentic swarm coding with GitHub Copilot |

### Emerging Tooling

| Tool | Purpose |
|------|---------|
| [CCManager](https://github.com/kbwo/ccmanager) | CLI for managing multiple Claude Code sessions across worktrees |
| Claude Squad | Multi-agent session management |
| SplitMind | Parallel agent orchestration |

### Scale in Practice

> "Developers report managing up to 10 Claude Code instances simultaneously, though most find 3-5 agents optimal."
> — [Geeky Gadgets](https://www.geeky-gadgets.com/how-to-use-git-worktrees-with-claude-code-for-seamless-multitasking/)

### Multi-Agent Frameworks

| Framework | Approach |
|-----------|----------|
| [CrewAI](https://blog.n8n.io/ai-agent-orchestration-frameworks/) | Role-based agents (Planner, Developer, Reviewer) |
| [MetaGPT](https://www.augmentcode.com/guides/spec-driven-ai-code-generation-with-multi-agent-systems) | Simulates PM, dev, QA roles |
| [AutoGen](https://learn.microsoft.com/en-us/agent-framework/overview/agent-framework-overview) | Microsoft's event-driven multi-agent |
| [Google ADK](https://developers.googleblog.com/en/agent-development-kit-easy-to-build-multi-agent-applications/) | Sequential, Parallel, Loop workflow agents |

### The Core Challenge

> "The difference between success and disaster comes down to one thing: do the agents understand your codebase before they start coordinating changes to it?"
> — [Augment Code](https://www.augmentcode.com/guides/what-is-agentic-swarm-coding-definition-architecture-and-use-cases)

This is why **foundation first** and **clear specs** matter.

---

## The Problem

In early-stage projects:
- Features share foundation code (critical path)
- Sequential implementation is slow
- Parallel implementation causes merge conflicts
- No coordination = duplicated work or stepping on each other

## The Solution: Layered Parallelization

```
  ┌──────────┐    ┌────────────┐    ┌─────────────┐    ┌───────────┐
  │   PLAN   │───▶│ FOUNDATION │───▶│ PARALLELIZE │───▶│ INTEGRATE │
  └──────────┘    └────────────┘    └─────────────┘    └───────────┘
   Define         Build critical    Worktrees +        Merge back
   features       path first        parallel agents    to main
```

| Phase | What | How |
|-------|------|-----|
| Plan | Define features, extract shared foundation | Architect creates manifest + specs |
| Foundation | Build critical path | Sequential (unavoidable) |
| Parallelize | Implement features | Worktree per feature, agent per worktree |
| Integrate | Merge back | Resolve conflicts, stabilize |

---

## Core Concept: The Manifest

A single source of truth that coordinates all agents.

### Location

```
/docs/features/
  manifest.md           # Root index - agents read this first
  foundation/
    spec.md             # Foundation specification
  features/
    feature-a.md        # Individual feature specs
    feature-b.md
```

### Manifest Structure

```markdown
# Feature Manifest

## Status Legend
- blocked - dependencies not complete
- ready - can start implementing
- in-progress - being worked on
- done - complete, merged to main

## Foundation

| Component | Status | Spec | Blocks |
|-----------|--------|------|--------|
| shared-types | done | foundation/spec.md | auth, tasks |
| core-utils | in-progress | foundation/spec.md | auth, tasks |

## Features

| Feature | Status | Spec | Depends On | Branch | Owns |
|---------|--------|------|------------|--------|------|
| auth | blocked | features/auth.md | core-utils | feat/auth | /src/auth/* |
| tasks | blocked | features/tasks.md | core-utils | feat/tasks | /src/tasks/* |

## Dependency Graph
```

```
                    shared-types [✅ done]
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
      core-utils [🔵 wip]        base-components [🔒]
              │                         │
       ┌──────┴──────┐                  ▼
       ▼             ▼            export [🔒]
   auth [🔒]    tasks [🔒]
```

**Legend:** ✅ done | 🔵 in-progress | 🔒 blocked (waiting on dependency)

### Why This Works

1. **Single source of truth** - All agents read same file
2. **Status tracking** - Prevents duplicate work
3. **Dependency graph** - Agents know what's blocked
4. **File ownership** - Prevents merge conflicts

---

## Agent Workflow

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│  ┌──────────────────┐                                           │
│  │ 1. Read manifest │                                           │
│  └────────┬─────────┘                                           │
│           ▼                                                     │
│  ┌──────────────────┐    No     ┌────────────┐                  │
│  │ 2. Ready items?  │─────────▶ │   Wait     │                  │
│  └────────┬─────────┘           └────────────┘                  │
│           │ Yes                                                 │
│           ▼                                                     │
│  ┌──────────────────┐                                           │
│  │ 3. Claim item    │  ← Update status: ready → in-progress     │
│  └────────┬─────────┘                                           │
│           ▼                                                     │
│  ┌──────────────────┐                                           │
│  │ 4. Read spec     │                                           │
│  └────────┬─────────┘                                           │
│           ▼                                                     │
│  ┌──────────────────┐                                           │
│  │ 5. Create        │  ← git worktree add ../proj-X -b feat/X   │
│  │    worktree      │                                           │
│  └────────┬─────────┘                                           │
│           ▼                                                     │
│  ┌──────────────────┐                                           │
│  │ 6. Implement     │  ← The actual coding work                 │
│  └────────┬─────────┘                                           │
│           ▼                                                     │
│  ┌──────────────────┐                                           │
│  │ 7. Merge to main │                                           │
│  └────────┬─────────┘                                           │
│           ▼                                                     │
│  ┌──────────────────┐                                           │
│  │ 8. Update        │  ← status → done, unblock dependents      │
│  │    manifest      │                                           │
│  └────────┬─────────┘                                           │
│           │                                                     │
│           └─────────────────────────────────────────────────────┘
│                         (loop back to step 1)
└─────────────────────────────────────────────────────────────────┘
```

### Agent Rules

| Rule | Why |
|------|-----|
| Only work on `ready` items | Blocked items have unmet dependencies |
| Claim before starting | Prevents two agents on same feature |
| Respect file ownership | Prevents merge conflicts |
| Update manifest when done | Unblocks dependent features |

---

## Git Worktree Setup

Worktrees let you have multiple branches checked out simultaneously in separate directories.

### Create Worktrees

```bash
# From main project directory
git worktree add ../project-auth -b feat/auth
git worktree add ../project-tasks -b feat/tasks
```

Result:

```
  File System                      Git Branches
  ────────────────────────         ────────────────
  ../project/            ◀─────▶   main
  ../project-auth/       ◀─────▶   feat/auth
  ../project-tasks/      ◀─────▶   feat/tasks
```

Each worktree = isolated workspace with its own branch. Same git history, separate working directories.

### Run Parallel Claude Instances

```bash
# Terminal 1
cd ../project-auth
claude "Implement auth feature per docs/features/features/auth.md"

# Terminal 2
cd ../project-tasks
claude "Implement tasks feature per docs/features/features/tasks.md"
```

### Merge Back

```bash
cd ../project
git checkout main
git merge feat/auth
git merge feat/tasks
```

### Cleanup

```bash
git worktree remove ../project-auth
git worktree remove ../project-tasks
git branch -d feat/auth feat/tasks
```

---

## Feature Spec Template

Each feature needs a clear spec so agents work independently.

```markdown
# Feature: [Name]

## Overview
[1-2 sentence description]

## Dependencies
- Requires: [list foundation components]
- Blocked by: [other features, if any]

## File Ownership
- Creates: /src/[feature]/*
- Modifies: [specific files only]
- DO NOT touch: [list other areas]

## Requirements
- [ ] Requirement 1
- [ ] Requirement 2

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2

## Technical Notes
[Any implementation guidance]
```

---

## Orchestration Commands

### Manual Orchestration

```bash
# 1. Check what's ready
grep "ready" docs/features/manifest.md

# 2. Create worktrees for ready features
git worktree add ../proj-auth -b feat/auth

# 3. Run agents
cd ../proj-auth && claude

# 4. After completion, update manifest and merge
```

### Automated Slash Command: `/implement-feature`

```markdown
1. Read manifest.md
2. Find feature by name
3. Validate status is "ready"
   - If blocked → STOP, report blocker
   - If in-progress → STOP, already claimed
   - If done → STOP, already complete
4. Update manifest: status → in-progress
5. Read feature spec
6. Create worktree
7. Implement per spec
8. Commit, push, create PR
9. Update manifest: status → done
10. Check if any blocked features become ready
```

### Automated Slash Command: `/orchestrate`

```markdown
1. Read manifest.md
2. Find ALL ready features
3. For each ready feature (in parallel):
   - Spawn agent: /implement-feature [name]
4. Wait for completion
5. Re-read manifest
6. Repeat until no ready items remain
```

---

## Example Timeline

```
Time    foundation    auth         tasks        export
────    ──────────    ────         ─────        ──────
T0      🟡 ready      🔒 blocked   🔒 blocked   🔒 blocked
        │
T1      🔵 working
        │
T2      ✅ done ──────┬────────────┐
                      │            │
T3                    🔵 working   🔵 working   🔒 blocked
                      │            │             (parallel!)
T4                    ✅ done      ✅ done ─────┐
                                                │
T5                                              🔵 working
                                                │
T6                                              ✅ done
```

**Key insight:** Foundation (sequential) unlocks auth + tasks (parallel). Export waits for both.

---

## Key Principles

### 1. Foundation First, Always

```
Parallel on unstable foundation = rewrite everything
```

Build foundation until it's stable enough that features won't need to modify it.

### 2. Clear File Ownership

```
Feature A owns /src/a/*
Feature B owns /src/b/*
No overlap = no conflicts
```

If features must share files, that code belongs in foundation.

### 3. Small Foundation

Don't over-engineer foundation. Build minimum needed to unblock features. You can always add more later.

### 4. Merge Often

Long-running branches diverge. Merge features as they complete, don't batch.

### 5. Manifest is Truth

Agents are stateless. They read manifest, find work, do work, update manifest. All coordination happens through the manifest file.

---

## Anti-Patterns

| Anti-Pattern | Problem | Fix |
|--------------|---------|-----|
| Parallelize before foundation stable | Features block on foundation changes | Finish foundation first |
| Features touching same files | Merge conflicts | Move shared code to foundation |
| No feature specs | Agents make inconsistent decisions | Write specs before implementing |
| Long branches (>3 days) | Hard to merge, divergence | Smaller features, merge often |
| Skipping manifest updates | Other agents don't know status | Always update after state change |

---

## When NOT to Parallelize

- Foundation still changing frequently
- Features have hidden dependencies
- Features are small (overhead > benefit)
- Solo developer (no benefit from parallelization)

---

## Checklist: Ready to Parallelize?

- [ ] Foundation is stable (no expected changes)
- [ ] Each feature has clear spec
- [ ] File ownership defined (no overlap)
- [ ] Manifest created with dependencies
- [ ] All blocked/ready statuses correct
- [ ] Worktree commands ready

---

## Quick Reference

### Commands

```bash
# Create worktree
git worktree add ../proj-[feature] -b feat/[feature]

# List worktrees
git worktree list

# Remove worktree
git worktree remove ../proj-[feature]

# Merge feature
git checkout main && git merge feat/[feature]
```

### Status Flow

```
  ┌─────────┐  dependency   ┌─────────┐  agent    ┌─────────────┐  merged   ┌──────┐
  │ blocked │─────done─────▶│  ready  │──claims──▶│ in-progress │─────────▶│ done │
  └─────────┘               └─────────┘           └─────────────┘          └──────┘
   Waiting on               Available for          Being worked on         Merged
   dependencies             agents to claim                                to main
```

### File Structure

```
/docs/features/
  manifest.md          # Coordination point
  foundation/
    spec.md
  features/
    [feature-name].md  # One per feature
```

---

## References

### Conversation Q&A

**Q: For a large project with many features sharing foundation as critical path, how to implement features in parallel using git worktrees?**

A: Use layered parallelization:
1. Plan → Define features + extract shared foundation
2. Foundation → Build critical path first (sequential)
3. Parallelize → One worktree per feature, separate Claude instances
4. Integrate → Merge features back to main

Key: Foundation must be stable before parallelizing. Each feature needs clear file ownership to prevent conflicts.

---

**Q: How to orchestrate this workflow? Idea: root file indexes features, agents read it to understand roadmap and blockers.**

A: Yes, use a **manifest file** as single source of truth:

```markdown
# manifest.md
| Feature | Status | Depends On | Owns |
|---------|--------|------------|------|
| auth | blocked | foundation | /src/auth/* |
```

Agent workflow:
1. Read manifest
2. Find `ready` items (not blocked)
3. Claim by updating status → `in-progress`
4. Implement
5. Update status → `done`
6. Check if dependents become unblocked

The manifest prevents:
- Working on blocked features
- Two agents on same feature
- File conflicts (via ownership column)

---

**Q: What's the general practice for any 0→1 project?**

A: Core rules:
1. **Foundation first** - No shortcut, parallel on shaky base = rewrite
2. **File ownership** - Each feature owns specific folders, no overlap
3. **Feature docs** - Each agent needs clear, scoped spec
4. **Merge often** - Don't let branches diverge >2-3 days
5. **Manifest updates** - Always update status after state changes

Anti-patterns to avoid:
- Parallelizing before foundation stable
- Features touching same files
- No scope docs for features
- Long-running branches

---

**Q: Is this industry practice?**

A: **Yes, it's emerging industry practice (2025).** Research findings:

**Who's doing it:**
- incident.io runs 4-5 Claude agents in parallel via worktrees
- Anthropic officially recommends worktree pattern
- Faire uses "agentic swarm coding" with multiple agents
- Developers report managing 3-10 agents (3-5 optimal)

**Dedicated tooling exists:**
- CCManager - CLI for managing Claude Code across worktrees
- Claude Squad, SplitMind - Multi-agent orchestration
- CrewAI, MetaGPT, AutoGen - Multi-agent frameworks

**The manifest approach aligns with frameworks:**
- CrewAI uses Planner/Developer/Reviewer roles
- MetaGPT simulates PM/dev/QA roles
- Google ADK has Sequential/Parallel/Loop workflow agents

**Core industry insight:**
> "The difference between success and disaster: do agents understand your codebase before coordinating changes?"

This validates: foundation first → clear specs → then parallelize.

---

## Sources

- [incident.io: Shipping faster with Claude Code and Git Worktrees](https://incident.io/blog/shipping-faster-with-claude-code-and-git-worktrees)
- [Anthropic: Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)
- [Blockhead: Git Worktrees + Claude Code Guide](https://www.blockhead.consulting/blog/Git_Worktrees_for_AI_Agents)
- [Agent Interviews: Parallel AI Coding with Git Worktrees](https://docs.agentinterviews.com/blog/parallel-ai-coding-with-gitworktrees/)
- [CCManager on GitHub](https://github.com/kbwo/ccmanager)
- [n8n: AI Agent Orchestration Frameworks](https://blog.n8n.io/ai-agent-orchestration-frameworks/)
- [Augment Code: Agentic Swarm Coding](https://www.augmentcode.com/guides/what-is-agentic-swarm-coding-definition-architecture-and-use-cases)
- [DevOps.com: Coding Agent Teams](https://devops.com/coding-agent-teams-the-next-frontier-in-ai-assisted-software-development/)
- [Anthropic: How We Built Our Multi-Agent Research System](https://www.anthropic.com/engineering/multi-agent-research-system)
- [Google: Agent Development Kit](https://developers.googleblog.com/en/agent-development-kit-easy-to-build-multi-agent-applications/)
