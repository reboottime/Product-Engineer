---
component: [Component Name]
category: [button|input|layout|feedback|navigation]
status: [draft|in-review|approved]
last-updated: YYYY-MM-DD
platforms: [chrome-extension, mobile-app, web]
---

# [Component Name]

## Overview

Brief description of the component and when to use it.

## Anatomy

Visual breakdown of component parts:

```
┌─────────────────────┐
│  [Icon] [Label]     │
└─────────────────────┘
```

### Parts

1. **Icon** (optional) - Purpose
2. **Label** - Purpose
3. **Container** - Purpose

## Variants

### Variant 1

[Description and use case]

### Variant 2

[Description and use case]

## States

- **Default** - Description
- **Hover** - Description
- **Active** - Description
- **Focused** - Description
- **Disabled** - Description
- **Error** - Description (if applicable)
- **Success** - Description (if applicable)

## Design Tokens

Reference design system tokens:

- Colors: `/shared/design-system/colors.md`
- Typography: `/shared/design-system/typography.md`
- Spacing: `/shared/design-system/spacing.md`

## Behavior

### Interactions

- Click/tap behavior
- Keyboard interactions (Tab, Enter, Space, etc.)
- Animations/transitions

### Responsive Behavior

How component adapts across screen sizes.

## Accessibility

### WCAG Compliance

- **Level**: AA / AAA
- **ARIA role**: [role]
- **ARIA attributes**: [list]

### Keyboard Navigation

- Tab: [behavior]
- Enter/Space: [behavior]
- Arrow keys: [behavior if applicable]

### Screen Reader

- Announcement: [what screen reader says]
- Live regions: [if applicable]

### Focus Management

[How focus works]

## Usage Guidelines

### When to Use

[Scenarios where this component is appropriate]

### When NOT to Use

[Scenarios where a different component is better]

### Best Practices

- Guideline 1
- Guideline 2
- Guideline 3

## Platform Adaptations

### Chrome Extension

[Any platform-specific variations]

### Mobile App

[Any platform-specific variations]

### Web

[Any platform-specific variations]

## Examples

### Example 1: [Use Case]

[Description and visual reference]

### Example 2: [Use Case]

[Description and visual reference]

## Implementation

### Component Props/API

```
{
  label: string
  variant: 'primary' | 'secondary'
  disabled: boolean
  // ... etc
}
```

### Code References

- Chrome Extension: [file path]
- Mobile: [file path]
- Web: [file path]

## Design Assets

- Figma: [link]
- Component library: [link]

## Related

- Related components: [list]
- Used in patterns: [list]
- Used in screens: [list]

## Changelog

- YYYY-MM-DD: [Change description]
