# Behavior Design Frameworks

Reference guide for product-design-lead agent. Apply these frameworks to create experiences that change behavior.

## 1. Fogg Behavior Model (B = MAT)

Behavior happens when **Motivation + Ability + Trigger** converge.

**Design implications:**

- **High motivation + low ability:** Simplify the action (reduce steps, pre-fill, smart defaults)
- **High ability + low motivation:** Increase triggers (visibility, reminders, social proof)
- **Both low:** Start with tiny habits, celebrate small wins

**Apply:** Identify user motivation level from requirements, then design for maximum ability (minimize steps, optimize for speed).

## 2. Habit Loop (Cue → Routine → Reward)

**Cue:** Make the trigger obvious
- Primary actions always visible (not hidden in menu)
- Visual reminders at key moments

**Routine:** Make the action easy
- Single-click primary actions (not multi-step flow)
- Minimal inputs for quick interactions

**Reward:** Make the benefit satisfying
- Completion celebrations (not just confirmations)
- Visual progress indicators

## 3. Friction as Feature

**Add friction to bad behaviors:**
- Strategic pauses before undesired actions
- Don't make it impossible (creates rebellion)
- Make it conscious (awareness prompts, not hard blocks)

**Remove friction from good behaviors:**
- Primary actions: <5 seconds to complete
- Critical paths: 1-2 clicks maximum
- Success confirmations: 1 click

## 4. Trust-Based Design

For behavior change tools, user agency > forced compliance

**Bad:** "Access Denied. [Action] blocked."
**Good:** "You're working on [goal]. Continue with [action]?"

Escape hatch available but with reflection moment.

## Content Voice Patterns

**Coach, not assistant:**
- "Start your first [action]" not "Would you like to [action]?"

**Action-oriented:**
- Verb-first buttons ("Start [action]" not "[Action]")

**Encouraging, not shaming:**
- "Keep going with [goal]" not "You failed"

## Microcopy Rules

- **Input fields:** Low barrier ("What are you working on?" not "Enter [field] description")
- **Progress messages:** Celebrate wins ("30 min completed!" not "15 min remaining")
- **Interruptions:** Supportive redirect ("Working on [goal]?" not "Access Denied")
- **Empty states:** Clear next action ("Add your first [item] to start" not "No [items]")

## Edge Cases Checklist

1. **First-time empty:** Onboarding flow, example content, clear CTA
2. **Returning empty:** Quick-add focused, no re-onboarding
3. **Errors:** Helpful message + retry CTA + fallback action
4. **Partial data:** Graceful degradation, don't block entire UI
5. **[Platform-specific]:** State persistence, background/foreground transitions
6. **[Platform-specific]:** Interruptions handling
