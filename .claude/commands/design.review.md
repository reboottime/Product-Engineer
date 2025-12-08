---
description: Review and iterate on existing design
argument-hint: [feature-name]
tags: [product, design]
---

# Review Design

Use the Task tool to invoke the founding-product-design-lead agent to review and update an existing design.

`subagent_type: founding-product-design-lead`

**Prompt**: "Review and iterate on $ARGUMENTS.

**Process:**
1. Find existing design spec:
   - Search: `docs/product/design/platforms/*/screens/$ARGUMENTS.md`
   - Or: `docs/product/design/screens/$ARGUMENTS.md`
2. Read current design
3. Ask user: "What needs to change?" (if not specified in context)
4. Update design based on feedback

**Output:**
- Use Lite Template for updates
- Show before/after for changed elements
- Explain rationale for changes
- Note impact on related screens/flows

**Common review types:**
- Microcopy changes
- Layout adjustments
- Adding/removing states
- Component updates
- Flow modifications

Update existing file or create version (v1.1, v1.2, etc.) if major changes."
