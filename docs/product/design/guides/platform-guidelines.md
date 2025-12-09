---
type: design-guide
topic: platform
purpose: Define platform-specific adaptations (iOS, Android, Web, etc.)
agents: [product-design-lead, founding-product-manager]
triggers: [adding second platform, platform-specific user complaints, OS major update]
related: [accessibility.md, design-principles.md]
status: template
---

# Platform Guidelines

How the product adapts to different platforms while maintaining brand consistency.

## Project Application

<!-- Update when: adding platform, platform-specific issues reported -->

**Target Platforms:**
- [ ] Web (desktop browser)
- [ ] Web (mobile browser)
- [ ] iOS native
- [ ] Android native
- [ ] Browser extension
- [ ] Desktop app (macOS/Windows)

**Primary Platform:** [Which platform do you design for first?]

**Cross-Platform Strategy:**
- [ ] Platform-native (follow each platform's guidelines strictly)
- [ ] Brand-consistent (same design across platforms, minor adaptations)
- [ ] Hybrid (shared design tokens, platform-specific components)

**Learnings:**
- [Date] - [Platform-specific issue discovered and how we adapted]

---

## Platform Design Systems

| Platform | Design System | Key Resource |
|----------|--------------|--------------|
| iOS | Human Interface Guidelines (HIG) | developer.apple.com/design |
| Android | Material Design 3 | m3.material.io |
| Web | No single standard | Follow accessibility (WCAG) |
| macOS | HIG for macOS | developer.apple.com/design |
| Windows | Fluent Design | learn.microsoft.com/design |

## Key Platform Differences

### Navigation

| Element | iOS | Android | Web |
|---------|-----|---------|-----|
| Back action | Top-left button or swipe | System back button | Browser back |
| Primary nav | Bottom tabs | Bottom nav or drawer | Top nav or sidebar |
| Secondary nav | Push to new screen | Navigate within hierarchy | Links, breadcrumbs |

### Components

| Element | iOS | Android | Web |
|---------|-----|---------|-----|
| Date picker | Scroll wheels | Calendar grid | Native or custom |
| Alerts | Centered modal | Dialog from bottom | Modal or toast |
| Low-priority messages | Banners | Snackbars | Toasts |
| Selection | Switches | Checkboxes/Switches | Checkboxes |

### Visual Style

| Aspect | iOS (HIG) | Android (Material) |
|--------|-----------|-------------------|
| Elevation | Flat design, minimal shadows | Shadows indicate hierarchy |
| Typography | SF Pro, strict sizing | Roboto, more flexibility |
| Icons | SF Symbols, outlined | Material icons, filled default |
| Motion | Subtle, physics-based | Expressive, meaningful |

### Screen Sizes

| Platform | Base Design Size | Notes |
|----------|-----------------|-------|
| iOS | 375×812pt | Consistent sizes, easier testing |
| Android | 360×640dp | Wide variety, needs more testing |
| Web | 1280px desktop, 375px mobile | Responsive breakpoints |

## Cross-Platform Principles

1. **Shared design tokens** - Colors, typography, spacing stay consistent
2. **Platform-native interactions** - Navigation, gestures follow platform conventions
3. **Feature parity** - Same core functionality, adapted UI
4. **Test on real devices** - Emulators miss platform-specific quirks

## When to Revisit

- Launching on new platform
- OS major version update (iOS 26, Android 15, etc.)
- Users report platform-specific confusion
- New device form factors (foldables, wearables)
