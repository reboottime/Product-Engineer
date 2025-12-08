---
description: Document anything learned into a human-friendly guide (project)
---

# Teach Command

You are creating a learning guide for humans in `/for-human/learning/`.

## Your Task

1. **Get the topic**: The user will provide either:
   - Something they just learned from our conversation
   - A topic/concept to explain
   - Insights or findings to document
   - A file path to convert

2. **Determine domain and name**:
   - Ask user for domain if not obvious (e.g., `claude-code`, `product-design`, `engineering`, `ai-agents`)
   - Create filename: `{domain}.{topic-slug}.md`
   - Examples: `claude-code.tool-use.md`, `product-design.wireframing.md`

3. **Create the guide** following these rules:

## Content Rules

**Structure:**

- **Scannable**: Headers, bullets, tables, code blocks
- **Practical**: Focus on "how" not "why theory"
- **Concise**: Short sections, no comprehensive explanations
- **Actionable**: Examples and quick reference

**Format:**

```markdown
# Title (What They'll Learn)

Brief intro (1-2 sentences max)

## Section 1: Core Concept

- Key point with example
- Key point with example

### Code Example (if relevant)

```language
// Practical, copy-paste ready code
```

## Section 2: Common Scenarios

| Scenario | Solution | When to Use |
|----------|----------|-------------|
| ... | ... | ... |

## Quick Reference

- Cheat sheet style
- Fast lookup

## Learn More

- [Relevant links]

```

**What to document:**

- Insights from conversations (product decisions, technical solutions)
- Research findings or competitive analysis
- New concepts, frameworks, or methodologies
- Lessons from testing or experimentation
- Best practices or patterns discovered
- Customer insights or user research

**Avoid:**

- Long prose paragraphs
- Comprehensive guides
- Theoretical discussions
- Essays or deep dives

## Output

1. Create file at `/for-human/learning/{domain}.{topic}.md`
2. Confirm to user: "Created learning guide at `for-human/learning/{filename}`"
3. Briefly describe what's inside (2-3 bullets)
