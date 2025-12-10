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

**Naming:** `YYYY-MM-DD.[domain].[descriptive-name].md`

Domains: `product`, `engineering`, `business`, `design`, etc.

Examples:
- `2025-12-09.product.mvp-feature-evaluation.md`
- `2025-12-09.engineering.architecture-proposal.md`
- `2025-12-09.business.market-analysis.md`

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

- `todo.md` and `todo.completed.md` are human's personal roadmap
  - Agents CAN add new tasks when explicitly requested
  - Agents CAN add context/details to existing tasks
  - Agents NEVER change task completion status (checking/unchecking boxes)
- Agents create topic-specific task files: `todo.setup.md`, `todo.testing.md`, `todo.[topic].md`
- Keep files small and focused (better clarity and effectiveness)
- Use same priority structure as todo.md (High/Medium/Low Priority)

**Checkbox format (required):**

- Use `- [ ]` for incomplete tasks, `- [x]` for completed
- NEVER use emoji checkmarks (`✅`, `☑️`, etc.) - breaks `/tidy-todo` automation
- Applies to all checklists in `/for-human/` files

## Content Standards

Keep all content concise (no comprehensive guides). Notify human, clear next steps, plain language, flag urgency.
