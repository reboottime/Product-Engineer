# Using the Product Design Lead Agent

Guide for collaborating with the product-design-lead agent in real-world design workflows.

## Quick Start

**Agent:** `product-design-lead`
**Purpose:** Design UX flows, wireframes, and specs in markdown
**Commands:** `/design.flow`, `/design.wireframe`, `/design.specs`, `/design.review`, `/design.component`

## When to Use

✅ **Use the design agent when:**
- Starting a new feature (need flows + wireframes)
- Iterating on existing designs
- Creating reusable components
- Need design specs for engineers

❌ **Don't use when:**
- Just need quick UI copy changes (do it yourself)
- Pixel-perfect visual design (agent does structure, not pixels)
- User research or testing (that's research work)

## Real-World Workflows

### Workflow 1: New Feature (Incremental Approach)

**Scenario:** Building "daily review" feature for productivity app

**Steps:**

1. **Start with flow**
   ```
   /design.flow daily-review
   ```
   - Agent reads requirements
   - Creates Mermaid flow diagram
   - You review, discuss decision points
   - Iterate until flow is clear

2. **Create wireframes**
   ```
   /design.wireframe daily-review
   ```
   - Agent creates 2-4 key screens (ASCII)
   - Shows layout and components
   - You give feedback on structure
   - Iterate on specific screens

3. **Full specification**
   ```
   /design.specs daily-review
   ```
   - Agent creates complete spec
   - All states (default, loading, error, empty)
   - Microcopy, interactions, rationale
   - Engineer can implement from this

**Why incremental:**
- Catch issues early (flow → wireframes → specs)
- Smaller outputs, easier to review
- More human input at each stage

### Workflow 2: Quick Iteration

**Scenario:** User feedback says error message is confusing

**Steps:**

1. **Review existing design**
   ```
   /design.review checkout-flow
   ```

2. **Agent asks:** "What needs to change?"

3. **You specify:** "Error state when payment fails needs clearer retry instructions"

4. **Agent updates:**
   - Shows before/after
   - Updates error microcopy
   - Adds retry button design
   - Saves v1.1

**Why this works:**
- Quick, focused updates
- No need to redesign entire flow
- Version history preserved

### Workflow 3: Building Component Library

**Scenario:** Creating reusable button component

**Steps:**

1. **Design component**
   ```
   /design.component button
   ```

2. **Agent creates:**
   - Variants: Primary, Secondary, Danger, Ghost
   - Sizes: Small, Medium, Large
   - States: Default, Hover, Active, Disabled, Loading
   - Props: label, icon, onClick, variant, size
   - Accessibility: ARIA labels, keyboard nav

3. **You review:**
   - Check variants cover use cases
   - Verify accessibility requirements
   - Confirm with design system

4. **Engineer implements** from shared component spec

**Why component-first:**
- Reusable across features
- Consistency in design system
- Engineers know where to look

### Workflow 4: Direct Agent Spawn (When Requirements Exist)

**Scenario:** Requirements already documented, need full design

**Steps:**

1. **Spawn agent directly**
   ```
   @product-design-lead Design the settings screen for user preferences
   ```

2. **Agent autonomously:**
   - Reads `/docs/product/requirements/settings.md`
   - Checks design principles and shared components
   - Creates complete design spec
   - Saves to appropriate location

3. **You get:** Full spec ready for engineering

**When to use:**
- Requirements are clear and complete
- You trust agent to make design decisions
- Want fast turnaround

**Risk:** Big output to review. If uncertain, use incremental workflow instead.

## Tips for Success

### 1. Prepare Requirements First

**Before designing:**
- Write PRD: `/pm.write-prd [feature]`
- User goal clear
- Success metrics defined

**Why:** Agent makes better decisions with context

### 2. Use AskUserQuestion Flow

Agent will ask when:
- Multiple valid approaches exist
- Requirements conflict
- Industry-specific decisions needed

**Your job:** Answer with context, not just preference

### 3. Reference Existing Patterns

**Before new design:**
```
Check: /docs/product/design/shared/components/
Check: /docs/product/design/shared/patterns/
```

**Why:** Consistency with existing design system

### 4. Iterate in Conversation

Don't spawn new agent each time. Instead:

```
You: /design.wireframe onboarding
Agent: [Shows 3 screens]

You: Screen 2 needs more emphasis on value prop
Agent: [Updates screen 2]

You: Better. Now show full specs
Agent: [Generates complete spec]
```

**Why:** Context carries through conversation

## Common Patterns

### Pattern: Design Sprint

**Day 1:** Flows for 3-5 features
```
/design.flow feature-1
/design.flow feature-2
/design.flow feature-3
```

**Day 2:** Wireframes for approved flows
```
/design.wireframe feature-1
/design.wireframe feature-2
```

**Day 3:** Full specs for approved wireframes
```
/design.specs feature-1
/design.specs feature-2
```

### Pattern: Component Audit

**Scenario:** Standardizing design system

```
/design.component button
/design.component input
/design.component card
/design.component modal
```

**Result:** Shared component library documented

### Pattern: Design Review Cycle

**Weekly iteration:**

```
Monday: Review metrics, identify issues
Tuesday: /design.review [problem-areas]
Wednesday: Engineer implements
Thursday: Test and gather feedback
Friday: Repeat
```

## Customization Per Project

### Industry-Specific Frameworks

**Edit:** `/docs/product/design/guides/principles.md`

**Examples:**

**Healthcare app:**
```markdown
## Design Framework: Safety-First

**Principles:**
- Confirmation for critical actions
- Clear medical disclaimers
- HIPAA-compliant data display
- Error prevention over error handling
```

**E-commerce:**
```markdown
## Design Framework: Conversion Optimization

**Principles:**
- Trust signals (reviews, security badges)
- Friction removal on checkout
- Clear pricing and shipping
- Social proof and urgency
```

**B2B SaaS:**
```markdown
## Design Framework: Efficiency-First

**Principles:**
- Keyboard shortcuts for power users
- Batch operations
- Advanced filters and search
- Data export options
```

### Platform-Specific

**Multi-platform project:**

Structure:
```
/docs/product/design/platforms/
  web/
  mobile-app/
  chrome-extension/
```

**Agent automatically:**
- Detects platform from requirements
- Applies platform constraints
- Saves to correct location

## Troubleshooting

### "Agent created huge file, can't review"

**Solution:** Use incremental commands
- `/design.flow` first (just flow)
- `/design.wireframe` next (structure only)
- `/design.specs` last (complete spec)

### "Design doesn't match existing patterns"

**Solution:** Reference shared components
```
Before designing, tell agent:
"Use button component from /shared/components/button.md"
```

### "Agent asked too many questions"

**Means:** Requirements unclear

**Fix:**
1. Write clearer PRD first
2. Define success metrics
3. Specify constraints upfront

### "Need design for engineering sprint tomorrow"

**Fast path:**
1. Check if requirements exist
2. Spawn agent directly: `@product-design-lead Design [feature]`
3. Review output
4. Quick iteration in same conversation
5. Done

**Trade-off:** Less collaborative, but faster

## Advanced: Agent Collaboration

### Design → Engineering Handoff

**Design agent creates:** `/docs/product/design/screens/feature.md`

**Engineer reads:** Spec has everything needed
- Component tree
- All states
- Interactions
- Microcopy

**No agent-to-agent communication needed**

### PM → Design → Engineering Flow

**PM validates:**
```
/pm.validate-feature user-profiles
Result: Build Now (RICE score: 850)
```

**PM writes PRD:**
```
/pm.write-prd user-profiles
```

**Designer creates:**
```
/design.flow user-profiles
/design.wireframe user-profiles
/design.specs user-profiles
```

**Engineer implements** from spec

**Seamless handoff, each agent reads previous output**

## Summary

**Incremental approach (recommended):**
1. `/design.flow` → Review flow
2. `/design.wireframe` → Iterate on structure
3. `/design.specs` → Get complete spec

**Fast approach (when requirements clear):**
- Spawn agent directly with full context
- Review large output
- Iterate in conversation

**Best practices:**
- Prepare requirements first
- Use shared components
- Customize design framework per industry
- Iterate in conversation, don't re-spawn

**Human role:**
- Provide context and requirements
- Make decisions at checkpoints
- Review and approve outputs
- Customize framework for project
