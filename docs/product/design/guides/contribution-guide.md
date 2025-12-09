---
type: design-guide
topic: contribution
purpose: Instructions for updating design guides
agents: [product-design-lead, founding-product-manager]
triggers: [before updating any guide, onboarding new contributor]
related: [design-principles.md, onboarding.md, accessibility.md, platform-guidelines.md]
status: stable
---

# Contribution Guide

How to contribute to design documentation.

## Who Updates What

| Role | Updates | When |
|------|---------|------|
| PM | Project Application sections, Learnings | After user research, feature launches |
| Design Lead | Principles, Patterns, Components | After design decisions, pattern emergence |
| Engineers | Technical constraints, Implementation notes | During/after implementation |

## How to Update Guides

### Adding a Learning

1. Open the relevant guide
2. Find the "Learnings" section under Project Application
3. Add entry: `- [Date] - [What happened and what we learned]`

Example:
```
- 2025-03-15 - Users confused by bottom nav on Android; switched to drawer pattern
```

### Promoting to General Principles

When a learning appears 2-3 times across projects:

1. Extract the pattern
2. Add to General Principles section
3. Keep original learnings as evidence

### Adding a New Principle

Format:
```markdown
### [Principle Name]

[One sentence: what it means and why it matters]

**Do:** [Concrete example]
**Don't:** [Counter-example]
```

## File Naming

- Use kebab-case: `design-principles.md`
- Be specific: `onboarding.md` not `ux.md`
- One topic per file

## Review Process

1. Make changes
2. Run `/design.update-guide [guide-name]` to validate
3. Commit with message: `docs(design): update [guide-name] - [what changed]`

## When NOT to Update

- Speculation (wait for evidence)
- One-off exceptions (document in project, not guides)
- Platform/tool-specific quirks (put in platform-guidelines.md instead)
