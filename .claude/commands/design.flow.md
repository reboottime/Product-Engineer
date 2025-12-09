---
description: Design user flow for a feature (step 1 of design process)
argument-hint: [feature-name]
tags: [product, design]
---

# Design User Flow

Use the Task tool to invoke the founding-product-design-lead agent to create a user flow diagram for the specified feature.

`subagent_type: founding-product-design-lead`

**Prompt**: "Create a user flow diagram for $ARGUMENTS.

**Process:**

1. Read `/docs/product/requirements/$ARGUMENTS.md` (if exists, otherwise ask user for context)
2. Extract user goal and success criteria
3. Create markdown-formatted flow showing:
   - Entry point
   - Decision points
   - Happy path + error paths
   - Exit points
4. Keep it high-level (5-10 steps max)

**Output:**

- If platform-specific: save to `/docs/product/design/platforms/[platform]/flows/[feature-name].md`
- If cross-platform: save to `/docs/product/design/flows/[feature-name].md`
- Markdown-formatted user flow with:
  - Brief description of each step
  - Open questions for user (if any)

**Do NOT:**

- Create wireframes yet (that's /design.wireframe)
- Write full spec (that's /design.specs)
- Assume requirements - ask if unclear

Present flow, ask for feedback before proceeding."
