# Design System Fundamentals

## What is a Design System?

A collection of reusable decisions, components, and guidelines that ensure visual and interaction consistency across a product.

## Core Elements

### 1. Visual Foundation

| Element | What to Define |
|---------|----------------|
| **Colors** | Primary, secondary, semantic (error/warning/success), neutrals, dark mode variants |
| **Typography** | Font families, size scale, line heights, font weights |
| **Spacing** | Consistent scale (4px, 8px, 16px, 24px...), padding/margin tokens |
| **Shadows** | Elevation levels for cards, modals, dropdowns |
| **Border radius** | Consistent rounding values (none, sm, md, lg, full) |
| **Icons** | Icon set choice, sizing conventions |

### 2. Component Library

**Primitives:**

- Buttons, inputs, checkboxes, radio buttons, toggles, selects

**Layout:**

- Grid system, containers, flex/stack utilities

**Feedback:**

- Alerts, toasts, loading states, progress indicators

**Navigation:**

- Tabs, breadcrumbs, menus, pagination

**Overlays:**

- Modals, dialogs, tooltips, popovers, sheets

**Data Display:**

- Tables, lists, cards, badges

### 3. Interaction Patterns

**States:** Default, hover, focus, active, disabled, loading, error

**Motion:**

- Duration scale (fast: 100ms, normal: 200ms, slow: 300ms)
- Easing curves (ease-in, ease-out, ease-in-out)
- When to animate vs. instant change

**Accessibility:**

- Keyboard navigation patterns
- Focus ring visibility
- Touch targets (minimum 44px for mobile)

### 4. Design Tokens

Named variables for all values, enabling consistency and theming:

```
--color-primary: #3B82F6
--spacing-md: 16px
--radius-lg: 12px
--shadow-card: 0 2px 8px rgba(0,0,0,0.1)
```

### 5. Documentation

- **Usage guidelines**: When to use each component
- **Do's and don'ts**: Common mistakes to avoid
- **Responsive breakpoints**: Mobile/tablet/desktop thresholds
- **Accessibility requirements**: Contrast ratios, ARIA patterns

## Who Decides the Design System?

| Role | Responsibility |
|------|----------------|
| **Product Designer** | Proposes system, ensures usability and consistency |
| **Engineers** | Feasibility input, implementation constraints |
| **Product Owner** | Final approval on brand/aesthetic direction |
| **Users** (indirectly) | Validation through usability testing |

In small teams: Often one person wears multiple hats. The key is documenting decisions so they're consistent across time, not just across people.

## When to Create/Update a Design System

### Create When:

| Trigger | Why |
|---------|-----|
| **First wireframes approved** | Tokens inform implementation; earlier = less rework |
| **New platform added** | Each platform (web, extension, mobile) needs platform-specific tokens |
| **Brand refresh** | Colors, typography, personality may all change |
| **Multiple people implementing UI** | Consistency requires shared reference |

### Update When:

| Trigger | Why |
|---------|-----|
| **Wireframes reveal gaps** | New screen needs color/spacing not yet defined |
| **User testing feedback** | "Too cramped", "Can't read text" → adjust tokens |
| **Accessibility audit** | Contrast ratios, touch targets may need fixes |
| **Platform constraints discovered** | iOS safe areas, browser extension limits |

### Don't Create/Update When:

| Situation | Instead Do |
|-----------|------------|
| **Before wireframes exist** | Wait—you'll guess wrong |
| **Single throwaway prototype** | Use framework defaults |
| **No UI changes planned** | Leave it alone |
| **"Just in case" future needs** | YAGNI—add when needed |

### POC/MVP Projects

For early-stage projects:

1. **Minimal viable design system** — Only tokens you'll actually use
2. **Platform-agnostic core** — Share what you can (colors, typography)
3. **Platform-specific when forced** — Extension popup ≠ web app viewport
4. **Update only when wireframes demand it** — Don't pre-optimize

## Optional Extensions

- **Theming**: Light/dark mode, brand color variants
- **Localization**: RTL support, text expansion for translations
- **Density modes**: Compact vs. comfortable spacing for different contexts
