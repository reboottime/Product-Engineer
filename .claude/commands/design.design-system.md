---
description: Create or update design system tokens for a platform
argument-hint: [platform]
tags: [product, design]
---

# Create/Update Design System

Use the Task tool to invoke the founding-product-design-lead agent to create or update design system tokens.

`subagent_type: founding-product-design-lead`

**Prompt**: "Create or update design system tokens for $ARGUMENTS.

**Context:**

- If `$ARGUMENTS` provided: Create/update tokens for that platform
- If no arguments: Review and update shared (platform-agnostic) tokens

**Process:**

1. Read `/docs/product/design/STRUCTURE.md` - **follow file paths exactly**
2. Read `/CLAUDE.md` for project context and target audience
3. Read `/docs/product/design/shared/design-system/README.md` for current architecture
4. Read wireframes from `/docs/product/design/platforms/[platform]/wireframes/` to understand UI needs
5. Check platform constraints from `/docs/technical/platforms/[platform].constraints.md` if exists

**Token Categories:**

Platform-agnostic (shared):

- Colors: Semantic palette optimized for target audience
- Typography: Font scale for platform constraints
- Spacing: Grid system with touch targets
- Motion: Animation durations with reduced motion fallbacks

Platform-specific (overrides):

- Dimension constraints (panel width, viewport)
- Layout calculations (component sizing)
- Platform API limits

**Output:**

- Shared tokens: `/docs/product/design/shared/design-system/[category].md`
- Platform tokens: `/docs/product/design/platforms/[platform]/design-tokens.md`
- Update README.md if architecture changes

**Requirements:**

- Document rationale for every decision
- Include accessibility compliance (contrast ratios, touch targets)
- Reference wireframes that informed decisions
- Keep minimal for current phase (expand post-validation)

**After completion:**

Create human review task at `/for-human/tasks/todo.design-system-review.md` with:

- Summary of changes
- Key decisions requiring approval
- Questions about tradeoffs"
