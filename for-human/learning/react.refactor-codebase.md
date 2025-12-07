# Refactoring Guidelines

## Universal Principles (All Languages)

**Core Rules:**
1. **Rule of Three** - Extract on 3rd use, not before
2. **YAGNI** - Don't build for hypothetical futures
3. **Wrong Abstraction > Duplication** - Bad abstractions harder to fix
4. **Single Responsibility** - One reason to change
5. **Locality** - Related code stays close (distance = cognitive cost)
6. **Extraction Criteria** - Need 2+ of: reused 3+ times, 50+ lines, complex logic, different change rate

**Universal Metrics:**
- Cyclomatic complexity > 10 → extract
- Function > 50 lines → consider split
- Parameters > 4 → use object/config
- Nesting > 4 levels → refactor

---

## What React Developers Often Miss

**1. Over-abstracting hooks** ⚠️
- **Universal principle violated:** Rule of Three
- **React-specific problem:** Custom hooks for single `useState` + `useEffect`
- **Fix:** Inline until 3rd use

**2. Component splits without reuse** ⚠️
- **Universal principle violated:** YAGNI
- **React-specific problem:** Extracting page-specific UI states into components
- **Fix:** Keep conditional renders inline (NoTimerState, LoadingState, etc.)

**3. Props drilling paranoia** ⚠️
- **Universal principle violated:** Premature optimization
- **React-specific problem:** Adding Context after 2 levels of props
- **Fix:** Props through 2-3 levels is fine, Context at 4+

**4. Performance optimization without profiling** ⚠️
- **Universal principle violated:** Measure before optimizing
- **React-specific problem:** `useMemo`/`useCallback` everywhere "just in case"
- **Fix:** Profile first, then optimize

**5. Configuration instead of composition** ⚠️
- **Universal principle violated:** Composition over inheritance/configuration
- **React-specific problem:** 15-prop components with boolean flags instead of composable children
- **React principle:** Composition is ALWAYS better - use children, slots, render props
- **Example:**
  ```tsx
  // ❌ Configuration (bad)
  <Modal
    title="Title"
    showHeader={true}
    showFooter={true}
    footerAlign="right"
    // ... 15 more props
  />

  // ✅ Composition (good)
  <Modal>
    <Modal.Header>Title</Modal.Header>
    <Modal.Body>Content</Modal.Body>
    <Modal.Footer align="right">Actions</Modal.Footer>
  </Modal>
  ```

**6. Missing co-location** ⚠️
- **Universal principle violated:** Locality
- **React-specific problem:** Splitting styles, logic, types across folders
- **Fix:** Keep feature code together

---

## Refactoring Decision Framework

```
┌─────────────────────────────────────┐
│ Is it used 3+ times?                │
│ NO → INLINE                         │
│ YES ↓                               │
├─────────────────────────────────────┤
│ Is it 50+ lines with single job?   │
│ NO → INLINE                         │
│ YES ↓                               │
├─────────────────────────────────────┤
│ Does it have complex logic?         │
│ (state + effects + calculations)    │
│ NO → INLINE                         │
│ YES ↓                               │
├─────────────────────────────────────┤
│ EXTRACT                             │
│ • Hook (logic reuse)                │
│ • Component (UI reuse)              │
│ • Utility (pure function)           │
└─────────────────────────────────────┘
```

**React-Specific Additions:**
- **Hooks:** Need complex state + effects (not just `useState`)
- **Components:** Need UI reuse across pages (not page-specific states)
- **Context:** Need 4+ level prop drilling (not 2-3 levels)
- **Memoization:** Need profiler evidence (not assumptions)
- **Composition:** ALWAYS prefer children/slots over prop configuration

---

## The Golden Rule

> "Make the change easy, then make the easy change" - Kent Beck

**Applied to React:**
1. Make it work (inline everything)
2. Identify real patterns (3+ uses)
3. Extract minimal abstractions
4. Compose over configure
