---
description: Generate full design specification (step 3 - after wireframes approved)
argument-hint: [feature-name]
tags: [product, design]
---

# Generate Design Specification

Use the Task tool to invoke the product-design-lead agent to create complete design specification for implementation.

`subagent_type: product-design-lead`

**Prompt**: "Create full design spec for $ARGUMENTS.

**Prerequisites:**
- User flow completed (or create if missing)
- Wireframes approved (or reference existing)

**Process:**
1. Read Claude.md for project context
2. Check `/docs/product/design/guides/principles.md` for design framework
3. Reference shared components from `/docs/product/design/shared/components/`
4. Create complete spec using Full Template from agent prompt

**Must include:**
- User goal and success metric
- User flow (Mermaid)
- Detailed wireframes with component trees
- All 4 states: Default, Loading, Error, Empty
- Microcopy for all UI text
- Interaction behaviors with timing
- Design rationale citing principles

**Output location:**
- Platform-specific: `/docs/product/design/platforms/[platform]/screens/$ARGUMENTS.md`
- Generic: `/docs/product/design/screens/$ARGUMENTS.md`

Save complete spec. Engineer can implement from this."
