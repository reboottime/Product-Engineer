---
description: Evaluate if a feature is worth building using RICE scoring (build now / later / never)
argument-hint: [feature-name]
tags: [product, validation, pm]
---

# Validate Feature

Use the Task tool to invoke the founding-product-manager agent to evaluate if a feature is worth building.

`subagent_type: founding-product-manager`

**Prompt**: "Validate $ARGUMENTS using RICE scoring (Reach, Impact, Confidence, Effort). Research, gather inputs, calculate score, check strategic alignment, and decide: Build Now / Build Later / Don't Build. Write to `/docs/product/decisions/$ARGUMENTS-validation.md`."
