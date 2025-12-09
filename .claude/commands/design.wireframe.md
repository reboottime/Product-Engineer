---
description: Create wireframes for a feature (step 2 of design process)
argument-hint: [feature-name]
tags: [product, design]
---

# Create Wireframes

Use the Task tool to invoke the founding-product-design-lead agent to create low-fidelity wireframes for the specified feature.

`subagent_type: founding-product-design-lead`

**Prompt**: "Create wireframes for $ARGUMENTS.

**Process:**

1. Read requirement or check if flow exists from /design.flow
2. Create ASCII wireframes for key screens (2-4 screens max)
3. Show layout and hierarchy only (no detailed copy yet)
4. Include component labels (buttons, inputs, cards, etc.)

**Output:**

- If platform-specific: save to `/docs/product/design/platforms/[platform]/wireframes/[feature-name].md`
- If cross-platform: save to `/docs/product/design/wireframes/[feature-name].md`
- Use this format per screen:

```
## Screen: [Name]

[ASCII wireframe]

**Key components:**
- [Component list]

**User can:**
- [Primary action]
- [Secondary actions]
```

**Do NOT:**

- Write detailed microcopy (that's /design.specs)
- Design all states yet (loading, error, empty)
- Create full design spec

Present wireframes, ask which screens need iteration."
