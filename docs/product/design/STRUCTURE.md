# Design Structure (ENFORCED)

All design agents MUST follow this structure exactly. Do not create files outside these paths.

## Shared (Platform-Agnostic)

```
/docs/product/design/shared/
  design-system/
    README.md           # Architecture overview
    SUMMARY.md          # Quick reference
    colors.md           # Color tokens
    typography.md       # Font scale
    spacing.md          # Grid & spacing
    motion.md           # Animation tokens
  components/
    _template.md        # Component template
    [name].md           # Reusable components
  patterns/
    README.md           # Pattern catalog
    [name].md           # Interaction patterns
```

## Platform-Specific

```
/docs/product/design/platforms/[platform]/
  README.md             # Platform overview
  design-tokens.md      # Platform overrides & constraints
  flows/
    [feature].md        # User flows
  wireframes/
    [feature].md        # ASCII wireframes (discovery)
    [feature]-[variant].md  # Variant wireframes
  screens/
    _template.md        # Screen template
    [feature].md        # High-fidelity screens (POC+)
  specs/
    _template.md        # Spec template
    [component].md      # Implementation specs
```

## Guides

```
/docs/product/design/guides/
  design-principles.md
  accessibility.md
  platform-guidelines.md
  contribution-guide.md
  onboarding.md
```

## Templates

```
/docs/product/design/templates/
  founding.wireframe.md   # Discovery phase template
  founding.screen.md      # POC phase template
```

## Naming Conventions

| Type | Pattern | Example |
|------|---------|---------|
| Feature files | `[feature].md` | `mvp-priority-enforcer.md` |
| Variants | `[feature]-[variant].md` | `onboarding-wizard.md` |
| Components | `[name].md` (kebab-case) | `task-card.md` |
| Platform folders | lowercase | `extension`, `mobile`, `web` |

## Current Platforms

- `extension` - Chrome Extension (Manifest V3)
- (Future: `mobile`, `web`)

## Rules

1. **Never create new top-level folders** - use existing structure
2. **Platform tokens override shared tokens** - shared is default, platform is specific
3. **One feature per file** - don't combine multiple features
4. **Use templates** - copy from `templates/` or `_template.md` files
5. **Update index.md** - after creating new files, update `/docs/product/design/index.md`
