# Update Design Guide

Update a design guide based on recent learnings.

## Input

$ARGUMENTS - Guide name: `onboarding` | `accessibility` | `platform` | `design-principles`

## Process

1. **Read guide metadata** - Open `/docs/product/design/guides/$ARGUMENTS.md`, check frontmatter:
   - `triggers` - Does current situation match?
   - `status` - Is it `template` (needs initial config) or `active/stable` (add learnings)?

2. **Check for new context**:
   - Recent user research in `/docs/product/research/`
   - Recent design decisions in `/for-human/intermediate/`
   - Current conversation context

3. **Evaluate** - Reference `/docs/product/design/guides/contribution-guide.md` "When NOT to Update":
   - Is this a pattern (seen 2+ times) or one-off?
   - Would this help future decisions?

4. **If nothing to add** - Report skip and stop.

5. **If update needed** - Determine type:
   - **Project Application**: Audience-specific adaptation or learning (add with date)
   - **General Principles**: Universal insight beyond this project
   - **Status change**: Update `status` in frontmatter if appropriate (`template` → `active`)

6. **Make the edit**

7. **Report**

## Output

Brief summary:

- Guide: [which guide]
- Action: [skipped / updated Project Application / updated General Principles]
- Change: [what was added, if any]

## Examples

**Skip case:**

```
Guide: onboarding
Action: Skipped
Reason: No new user testing since last update. Current "Nickel Tour" pattern still matches our simple MVP.
```

**Update case:**

```
Guide: onboarding
Action: Updated Project Application
Change: Added learning from 12/9 user test - "Users ignored permission request when shown on first screen. Moving to after first value moment increased grant rate 3x."
```
