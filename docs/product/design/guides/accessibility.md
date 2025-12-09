---
type: design-guide
topic: accessibility
purpose: Define accessibility requirements and compliance level
agents: [product-design-lead, founding-product-manager]
triggers: [regulated market entry, user accessibility complaint, scaling beyond early adopters, new platform launch]
related: [platform-guidelines.md]
status: template
---

# Accessibility Guidelines

Ensure the product is usable by people with disabilities.

## Project Application

<!-- Update when: entering regulated market, accessibility complaint received, adding platform -->

**Target Level:** [ ] A (minimum) / [ ] AA (standard) / [ ] AAA (comprehensive)

**WCAG Version:** [ ] 2.1 / [ ] 2.2

**Platforms:**

- [ ] Web
- [ ] Mobile
- [ ] Browser extension
- [ ] Desktop app

**Priority User Segments:**

- [ ] Vision (screen readers, color blindness, low vision)
- [ ] Motor (keyboard-only, limited dexterity)
- [ ] Cognitive (attention, memory, learning)
- [ ] Hearing (captions, transcripts)

**Testing Approach:**

- [ ] Automated tools (Axe, Lighthouse)
- [ ] Manual review
- [ ] User testing with assistive tech users

**Learnings:**

- [Date] - [What we learned and how it changed our approach]

---

## Core Principles (POUR)

### 1. Perceivable

Users must be able to perceive content through at least one sense.

- Alt text for images
- Captions for video/audio
- Sufficient color contrast (4.5:1 for text)
- Don't rely on color alone to convey meaning

### 2. Operable

Users must be able to navigate and interact.

- All functionality available via keyboard
- Skip links for navigation
- Touch targets minimum 44x44px
- No content that flashes >3 times/second

### 3. Understandable

Content and navigation must be clear.

- Plain language
- Consistent navigation
- Clear error messages with suggestions
- Labels on form inputs

### 4. Robust

Content works with assistive technologies.

- Valid HTML
- Semantic markup (headings, landmarks, lists)
- ARIA labels where needed
- Test with screen readers

## When to Revisit This Guide

- Entering regulated market (gov, healthcare, education)
- User reports accessibility issue
- Expanding to new platform
- International expansion
