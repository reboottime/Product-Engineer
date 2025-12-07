---
description: Sync implementation changes to product documentation
argument-hint: [file-path] (optional, can use conversation context)
tags: [product, documentation, sync, pm, design]
---

# Sync Features to Docs

Use the Task tool to invoke the product-manager agent to sync implementation changes back to product documentation.

`subagent_type: product-manager`

**Prompt**: "Analyze implementation changes from $ARGUMENTS or conversation context. Update related PRDs for functional changes. After updating PRDs, refresh `/docs/product/requirements/index.md` by reading all PRD frontmatter. Spawn product-design-lead for UI/UX changes to design specs."
