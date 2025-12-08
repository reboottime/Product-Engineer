---
description: Prepare handoff from founding PM (0→1) to growth PM (scaling phase)
agent: founding-product-manager
---

# Founding PM → Growth PM Handoff

You're transitioning from Discovery/POC to MVP/Production phase. Prepare complete handoff materials.

## Handoff Checklist

Execute in order:

1. **Validate readiness**
   - Read `/docs/product/strategy.md` → Confirm phase transition criteria met
   - Check POC metrics → Core action completion >20%, activation validated
   - If not ready: Stop, explain gaps, recommend what to validate first

2. **Document validated insights**
   - Review `/docs/product/research/interviews/` and `/docs/product/research/insights/`
   - Create `/docs/product/research/validated/handoff-YYYY-MM-DD.md`:
     - Validated problem (evidence from interviews)
     - Target segments (who, behaviors, pain points)
     - Value propositions (what resonated, what didn't)
     - Feature validation results (what worked, what failed, why)
     - Key learnings (surprises, pivots, invalidated assumptions)

3. **Create metrics baseline**
   - Analyze POC metrics
   - Create `/docs/product/metrics/baseline.md`:
     - Activation rate (current)
     - Core action completion (current)
     - Retention indicators (if available)
     - User feedback themes
     - Benchmark for growth PM to improve against

4. **Update strategy**
   - Edit `/docs/product/strategy.md`:
     - Update phase: Discovery/POC → MVP/Production
     - Document validated segments
     - Update roadmap with validated features
     - Note: Kill unvalidated items from roadmap

5. **Create handoff brief**
   - Create `/docs/product/handoff-brief.md`:

     ```markdown
     # Founding PM → Growth PM Handoff Brief

     **Date:** [YYYY-MM-DD]
     **Phase:** Discovery/POC → MVP/Production

     ## What We Validated

     **Problem:** [1-2 sentences]
     **Evidence:** [Interview count, completion rates, key quotes]

     ## Who We're Building For

     **Primary segment:** [Description]
     - Behaviors: [Key behaviors observed]
     - Pain points: [Validated pain points]
     - Value prop: [What resonates]

     **Secondary segment:** [If applicable]

     ## What We Built

     **Core features:** [List with validation results]
     **Killed features:** [What we cut and why]

     ## Metrics Baseline

     - Activation: [X%]
     - Core action: [X%]
     - Retention: [X% if available]

     ## Growth PM Focus Areas

     **Optimize:** [What's working but needs improvement]
     **Experiment:** [Hypotheses to test]
     **Watch:** [Risks or unknowns to monitor]

     ## Open Questions

     [Unvalidated assumptions to test in MVP phase]
     ```

6. **Archive POC work**
   - Move POC requirements to `/docs/product/requirements/archive/poc/`
   - Keep validated requirements in `/docs/product/requirements/`

## Output

Present handoff summary:

- Readiness status (ready/not ready + reasoning)
- Files created/updated
- Key insights for growth PM (3-5 bullets)
- Recommended next actions for growth PM

## If Not Ready

Don't proceed with handoff. Instead:

- List gaps (what's not validated)
- Recommend validation approach (interviews, experiments)
- Estimate: How many interviews/weeks to validate?
