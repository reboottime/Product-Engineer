---
type: index
path: docs/product/design/guides
agents: [product-design-lead, founding-product-manager]
---

# Design Guides

Design principles, guidelines, and best practices for the product.

## For LLM Agents

**When to read guides:** Check `triggers` field in each guide's frontmatter.

**Frontmatter schema:**

```yaml
type: design-guide
topic: [identifier]
purpose: [one-line description]
agents: [which agents use this]
triggers: [when to consult]
related: [cross-references]
status: template | active | stable
```

**Status meanings:**

- `template` - Unconfigured, use general principles only
- `active` - Project Application configured, actively evolving
- `stable` - Mature, rarely changes

## How Guides Evolve

Each guide has two layers:

1. **General Principles** - Industry best practices (stable baseline)
2. **Project Application** - Audience-specific adaptations (evolves with learnings)

**Workflow:**

1. PM/Design Lead apply general principles to project
2. Document chosen approach in "Project Application" section
3. After user testing/research, add learnings
4. If a learning is generalizable, promote it to general principles

## Contents

| Guide | Purpose | Triggers |
|-------|---------|----------|
| `design-principles.md` | Core product design principles | After 2-3 features, inconsistent decisions |
| `onboarding.md` | First-run experience design | Designing onboarding, user drop-off |
| `accessibility.md` | WCAG compliance requirements | Regulated market, accessibility complaints |
| `platform-guidelines.md` | iOS/Android/Web adaptations | Adding platform, platform-specific issues |
| `contribution-guide.md` | How to update guides | Before any guide update |

## Related

- Update guides: `/design.update-guide [guide-name]`
- Design specs: `/docs/product/design/platforms/`
- Human learning: `/for-human/learning/product-design.when-to-update-design-guides.md`
