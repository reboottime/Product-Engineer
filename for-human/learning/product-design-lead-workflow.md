# Product Design Lead Agent - Workflow Guide

## What This Agent Does

Designs user experiences using behavior change principles. Outputs markdown-based wireframes, flows, and specs that engineers implement directly.

## When It Runs

**After PM writes requirements**, before engineering starts.

## Input → Process → Output

### Takes In
- Requirements file from `/docs/product/requirements/[feature].md` (written by PM)
- Platform constraints from `CLAUDE.md`
- Existing design patterns from `/docs/product/design/screens/` for consistency

### Process
1. **Apply behavior lens** - Identify motivation/ability barriers, friction points, habit loops
2. **Design flow** - Mermaid diagram for complex flows (4+ steps)
3. **Create wireframes** - ASCII layouts with component trees (Tailwind classes)
4. **Define states** - Default, loading, error, empty (all required)
5. **Write microcopy** - Headers, CTAs, empty states, error messages
6. **Document rationale** - Cite behavior principles for key decisions

### Outputs
**Single artifact:** `/docs/product/design/screens/[feature-name].md`

Contains:
- User flow diagram
- ASCII wireframes
- Component trees with Tailwind classes
- All 4 states + interactions + timing
- Microcopy (exact copy)
- Design rationale

## Collaboration Model

**Async handoff, no meetings:**

```
PM writes requirements → Design Lead produces spec → Engineer implements
```

**Design Lead asks you questions only when:**
- Requirements conflict or are ambiguous
- 2+ equally valid approaches with different tradeoffs
- Major UX decision with business impact

**Otherwise:** Agent decides autonomously (layout, navigation, microcopy, component selection, friction points)

## What Makes This Different

**Behavior-first design:**
- Not just layouts - designs for habit formation and behavior change
- Applies Fogg Behavior Model (Motivation × Ability × Trigger)
- Uses friction as a feature (e.g., trust-based blocking vs hard blocking)

**Engineer-ready specs:**
- Component trees with actual class names
- Exact microcopy (not placeholders)
- All states defined (not just happy path)
- Interaction timing specified

## Example Flow

1. **PM writes** `/docs/product/requirements/task-quick-add.md`
2. **Design Lead reads** requirement + CLAUDE.md constraints
3. **Design Lead produces** `/docs/product/design/screens/task-quick-add.md` with:
   - Flow: User clicks "+" → Input appears → Enter task → Auto-focus timer
   - Wireframe: ASCII layout of popup with input placement
   - States: Empty (CTA visible), Typing (validation), Error (retry path), Success (transition)
   - Microcopy: "What are you working on?" (not "Enter task description")
   - Rationale: Single-input reduces friction (Fogg: high motivation, maximize ability)
4. **Engineer reads spec** and implements without needing clarification

## Output Location

All design specs saved to: `/docs/product/design/screens/[feature-name].md`

Engineers read these files to implement features.
