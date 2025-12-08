# Creating Content for Humans

## `/for-human/learning/`

Tutorials/guides for complex concepts or synthesized research.

**Naming:** `[domain].topic.md`

Examples:

- `product-design.process.md`
- `engineering.testing.md`
- `ai-agents.context-structure.md`

## `/for-human/intermediate/`

Work-in-progress analysis requiring human review/decision.

Use for: Evaluations, proposals, comparative analysis, draft recommendations

**Not for:** Final documentation (→ learning/), operational guides (→ manuals/), action items (→ tasks/)

**Task tracking rule:**

When creating intermediate/ content, ALWAYS create corresponding task in `/for-human/tasks/todo.[topic].md`:

```markdown
## Review: [Document Name]

**Location:** `/for-human/intermediate/[filename].md`

**Action needed:** Review and decide: [Accept/Revise/Reject]

**Context:** [1-2 sentences why this exists]
```

Prevents intermediate/ from accumulating untracked work.

## `/for-human/manuals/`

How-to guides for tools/processes humans maintain.

## `/for-human/tasks/`

Action items requiring human decision or follow-up.

**Critical rules:**

- `todo.md` and `todo.completed.md` are human's personal roadmap - agents NEVER modify these
- Agents create topic-specific task files: `todo.setup.md`, `todo.testing.md`, `todo.[topic].md`
- Keep files small and focused (better clarity and effectiveness)
- Use same priority structure as todo.md (High/Medium/Low Priority)

## Content Standards

Keep all content concise (no comprehensive guides). Notify human, clear next steps, plain language, flag urgency.
