---
description: Create detailed product requirements document for a validated feature
argument-hint: [feature-name]
tags: [product, prd, requirements, pm]
---

# Write PRD

Use the Task tool to invoke the founding-product-manager agent to write a Product Requirements Document (PRD).

`subagent_type: founding-product-manager`

**Prompt**: "Write PRD for $ARGUMENTS defining WHAT to build and WHY. Verify validation exists, gather context, and write to `/docs/product/requirements/$ARGUMENTS.md`. After writing PRD, update `/docs/product/requirements/index.md` by reading all PRD frontmatter and creating summary table (feature, status, priority, owner, last_updated). Offer to spawn product-design-lead for UX design."
