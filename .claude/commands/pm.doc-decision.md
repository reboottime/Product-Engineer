---
description: Document product decision (human + product-manager collaboration)
tags: [product, decision, pm]
---

# Document Decision

Invoke the product-manager agent to work with human on documenting a product decision.

Use Task tool with `subagent_type: product-manager` and prompt:

"Human made a product decision with your guidance. Document it in `/docs/product/decisions/[yyyy-mm-dd].[topic].md` following `_template.md` and update `index.md`.

CRITICAL: DO NOT read past decision files. Only read:
- `_template.md` (for structure)
- `index.md` (to add new row to catalog table)

When updating index.md, add only a single new row to the catalog table with metadata from the current decision.

CRITICAL: TL;DR must be written for humans (end users), not PMs. Focus on what the user experiences, not technical concepts. Use concrete examples.
- BAD: 'Single global timer for simplicity - reduces cognitive load'
- GOOD: 'When you switch tasks, you get a fresh 45-minute timer. Example: Task A at 23 min → click Task B → starts at 45:00'"
