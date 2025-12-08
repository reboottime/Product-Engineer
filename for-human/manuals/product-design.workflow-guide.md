# Design Lead Workflow

## Overview

The design lead agent creates UX specs after PM has validated requirements. This guide shows the real-world workflow from idea to implementation-ready design.

## Quick Reference

```sh
Idea → PM validates → PM writes PRD → Design creates specs → Engineering implements
```

## Detailed Workflow

### 1. After PM Writes Requirements

**Prerequisite:** PM has completed `/pm.write-prd [feature-name]`

- Creates `/docs/product/requirements/[feature-name].md`
- Defines WHAT to build and WHY
- Includes success metrics and constraints

**PM offers:** "Spawn product-design-lead for UX design?"

### 2. Design Process (3 Steps)

#### Step 1: User Flow

**Command:** `/design.flow [feature-name]`

**Agent does:**

- Reads `/docs/product/requirements/[feature-name].md`
- Creates high-level flow (5-10 steps)
- Shows entry/exit points, decision points, happy/error paths
- Presents flow for feedback

**You review:** Flow makes sense? All paths covered?

---

#### Step 2: Wireframes

**Command:** `/design.wireframe [feature-name]`

**Agent does:**

- References approved flow
- Creates ASCII wireframes (2-4 key screens)
- Shows layout, hierarchy, component labels
- NO detailed copy or all states yet (that's next)

**You review:** Layout works? Components clear? Iterate if needed.

---

#### Step 3: Full Design Spec

**Command:** `/design.specs [feature-name]`

**Agent does:**

- Reads `Claude.md` for project context
- Checks `/docs/product/design/guides/principles.md` for design framework
- References shared components from `/docs/product/design/shared/components/`
- Creates complete implementation spec

**Output:** `/docs/product/design/platforms/[platform]/screens/[feature-name].md` (or `/screens/` if generic)

**Includes:**

- User goal + success metric
- User flow (Mermaid diagram)
- Detailed wireframes + component trees
- All 4 states: Default, Loading, Error, Empty
- Complete microcopy (headers, CTAs, errors, empty states)
- Interaction behaviors with timing
- Design rationale citing principles

**Engineering uses this to implement** (no further design collaboration needed).

---

### 3. After Design Spec Complete

**Handoff:** Engineer implements from spec at `/docs/product/design/.../[feature-name].md`

**If changes needed:** `/design.review [feature-name]` for iterations

**After launch:** PM runs `/pm.review-feature [feature-name]` (2-4 weeks post-launch)

## When to Use Each Command

| Situation | Command | Output |
|-----------|---------|--------|
| Just starting design | `/design.flow` | High-level user flow |
| Flow approved, need screens | `/design.wireframe` | ASCII wireframes |
| Wireframes approved, ready for dev | `/design.specs` | Complete spec for implementation |
| Design exists, needs changes | `/design.review` | Updated spec |

## Decision Points

**Design lead decides autonomously:**

- Layout, visual hierarchy, components
- Navigation patterns, interactions
- Microcopy, content structure, tone
- Behavior triggers, friction points

**Design lead asks you:**

- Ambiguous requirements
- Multiple valid approaches with tradeoffs
- Industry compliance (HIPAA, financial, legal)

**Design lead escalates:**

- Missing requirements file
- Privacy/compliance concerns

## File Locations

**Inputs:**

- Requirements: `/docs/product/requirements/[feature].md`
- Design principles: `/docs/product/design/guides/principles.md`
- Shared components: `/docs/product/design/shared/components/`

**Outputs:**

- Platform-specific: `/docs/product/design/platforms/[platform]/screens/[feature].md`
- Generic: `/docs/product/design/screens/[feature].md`

## Tips

**Skip steps if appropriate:**

- Simple feature? Jump straight to `/design.specs`
- Just need flow? Stop after `/design.flow`
- Design is in your head? Tell agent "skip to specs, here's what I want..."

**Iterate freely:**

- "Add error state for network timeout"
- "Change CTA copy to be more action-oriented"
- "Show empty state with illustration, not just text"

**Reference existing:**

- "Use the same pattern as login screen"
- "Apply design system from /shared/components"
- "Match tone from onboarding flow"
