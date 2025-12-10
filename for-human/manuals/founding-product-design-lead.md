# Product Design Lead - Quick Reference

## Quick Start

**Agent invocation:**

```
@agent-product-design-lead [your instruction]
```

**Examples:**

- `design user flow for [feature]`
- `create wireframes for [feature]`
- `generate full design spec for [feature]`

**Slash commands (sequential workflow):**

| Step | Command | Purpose |
|------|---------|---------|
| **1** | `/design.flow [feature-name]` | User flow diagram (5-10 steps) |
| **2** | `/design.wireframe [feature-name]` | Low-fidelity wireframes (2-4 screens) |
| **3** | `/design.specs [feature-name]` | Full design specification for implementation |
| **Review** | `/design.review [feature-name]` | Iterate on existing design |
| **System** | `/design.design-system [platform]` | Create/update design tokens (colors, typography, spacing, motion) |

**Use for:** UX design in markdown (ASCII wireframes, Mermaid flows), design system tokens. Applies behavior design principles.

**Won't do:** Code implementation, marketing design

## What It Needs

- PRD from `/docs/product/requirements/[feature].md` (or context from user)
- Design principles from `/docs/product/design/guides/principles.md` (optional)
- Project context from `/CLAUDE.md`

## What You Get

| Command | Output Location | Contents |
|---------|----------------|----------|
| `design.flow` | Terminal output | Mermaid flow (entry → decisions → exit) |
| `design.wireframe` | Terminal output | ASCII wireframes, component labels, key actions |
| `design.specs` | `/docs/product/design/platforms/[platform]/screens/[feature].md` OR `/docs/product/design/screens/[feature].md` | Complete spec: flow + wireframes + states + microcopy + interactions |
| `design.review` | Updates existing spec | Version history, before/after, impact notes |
| `design.design-system` | Shared: `/docs/product/design/shared/design-system/` Platform: `/docs/product/design/platforms/[platform]/design-tokens.md` | Design tokens (colors, typography, spacing, motion) + human review task |

## Design Process (Sequential)

```
Step 1: /design.flow → Get approval →
Step 2: /design.wireframe → Get approval →
Step 3: /design.specs → Save to /docs/product/design/
```

**Iteration:** `/design.review` updates existing specs

## What's in a Full Spec

| Section | Contents |
|---------|----------|
| **User Goal** | What user accomplishes + success metric |
| **User Flow** | Mermaid diagram (if ≥4 steps) |
| **Wireframes** | ASCII + component tree + interactions |
| **4 States** | Default, Loading, Error, Empty |
| **Microcopy** | Headers, CTAs, errors, empty states |
| **Interactions** | Click behaviors, transitions, timing |
| **Rationale** | Design decisions + principles cited |

## Agent Decision Authority

**Decides autonomously:**

- Layout, hierarchy, components, navigation
- Microcopy, content structure, tone
- Behavior triggers, friction design

**Consults you (AskUserQuestion):**

- Ambiguous requirements (2+ valid approaches)
- Industry compliance (HIPAA, financial, legal)
- Tradeoff decisions

**Escalates:**

- Missing requirements file
- Privacy/compliance concerns

## Common Workflows

### New Feature Design (Full Process)

| Step | Action | Output |
|------|--------|--------|
| 1 | `/design.flow [feature]` | Flow diagram presented for approval |
| 2 | Human approves or requests changes | Iteration until approved |
| 3 | `/design.wireframe [feature]` | Wireframes presented for approval |
| 4 | Human approves or requests changes | Iteration until approved |
| 5 | `/design.specs [feature]` | Complete spec saved to `/docs/product/design/` |
| 6 | Human implements from spec | - |

### Design System (When Needed)

| Scenario | Command |
|----------|---------|
| New platform | `/design.design-system [platform]` |
| Update shared tokens | `/design.design-system` (no args) |
| After wireframes reveal token gaps | `/design.design-system [platform]` |

### Quick Design (Skip Steps)

```
Already have flow? → Start at /design.wireframe
Flow + wireframes ready? → Jump to /design.specs
```

### Iteration

```
/design.review [feature] → Agent asks what changed → Updates spec
```

## Output Locations

| Type | Platform-Specific | Platform-Agnostic |
|------|------------------|-------------------|
| **Screens** | `/docs/product/design/platforms/[platform]/screens/` | `/docs/product/design/screens/` |
| **Shared Components** | `/docs/product/design/shared/components/` | Same |
| **Design System** | `/docs/product/design/platforms/[platform]/design-tokens.md` | `/docs/product/design/shared/design-system/` |
| **Guides** | `/docs/product/design/guides/` | Same |

**Example platform values:** `extension`, `web-app`, `mobile-ios`, `mobile-android`

## Collaboration with PM

**PM writes PRD → Designer reads PRD → Designer creates UX spec**

| Scenario | Workflow |
|----------|----------|
| PM proposes feature | `/pm.propose-feature` invokes both PM + designer in parallel |
| PRD exists | Designer references `/docs/product/requirements/[feature].md` |
| No PRD | Designer asks human for context |
| Implementation changes UX | `/pm.sync-features` triggers designer to update specs |

## Design Principles Applied

Agent references these if they exist in `/docs/product/design/guides/principles.md`:

- Behavior design (triggers, motivation, ability)
- ADHD-specific UX patterns (if applicable)
- Accessibility standards
- Platform conventions

**If missing:** Uses standard UX principles

## Common Fixes

| Problem | Solution |
|---------|----------|
| Can't find requirements | Provide context or create PRD first with `/pm.write-prd` |
| Wrong output location | Check `/docs/product/design/README.md` for structure |
| Missing design principles | Agent uses standard UX principles |
| Needs iteration | Use `/design.review [feature]` not `/design.specs` |
| Wireframes too detailed | That's expected in step 3 (/design.specs), not step 2 |
| Missing design tokens | Use `/design.design-system [platform]` to create |
| Tokens need updating | Use `/design.design-system` to update shared or platform tokens |

## Version Control

**New features:** Version: v1.0 | Date: YYYY-MM-DD

**Updates:**
```markdown
Version: v1.1 | Date: YYYY-MM-DD

## Changes in v1.1
- [What changed]
- [Why it changed]
- [Impact on implementation]
```

---

**Full agent prompt:** `/Users/kate/future/anchor/.claude/agents/product-design-lead.md`

**Design folder structure:** `/docs/product/design/README.md`
