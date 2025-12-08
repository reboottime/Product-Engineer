---
description: Propose feature idea - PM & design lead collaborate to evaluate and decide
argument-hint: [feature-idea-or-scenario]
tags: [product, feature, collaboration, pm, design]
agent: founding-product-manager, founding-product-design-lead
---

# Propose Feature

Coordinate a collaborative evaluation between founding-product-manager and founding-product-design-lead to assess a feature idea and reach a decision.

You are the facilitator. Follow this workflow:

1. **Phase 1: Independent Deliberation (Parallel)**

   CRITICAL: Invoke both agents IN PARALLEL using a single message with multiple Task tool calls. Do NOT invoke sequentially.

   **PM Agent - Independent Analysis:**
   - Use Task tool with `subagent_type: founding-product-manager`
   - Prompt: "TASK: Engage in at least 3 rounds of independent deliberation on this feature idea. Do NOT see Design's input yet.

   FEATURE: $ARGUMENTS

   DELIBERATION REQUIREMENTS:
   Round 1: Present RICE score breakdown and initial Build Now/Later/Never recommendation
   Round 2: Challenge your own assumptions - what could go wrong? What are we missing?
   Round 3: Consider alternative approaches, edge cases, user segments. Does this fit MVP phase?
   Round 4+: Continue until high confidence in recommendation

   FOR EACH ROUND:
   - State which round you're in
   - Present new insights, not repetition
   - Challenge assumptions from previous round
   - Consider data/research that would validate or invalidate

   FINAL REPORT:
   - Decision: Build Now/Later/Never with clear rationale
   - Key insights from deliberation
   - Risks and mitigations
   - Success metrics to validate (if Build Now/Later)
   - What would change this decision"

   **Design Lead Agent - Independent Analysis:**
   - Use Task tool with `subagent_type: founding-product-design-lead`
   - Prompt: "TASK: Engage in at least 3 rounds of independent deliberation on this feature from UX/design perspective. Do NOT see PM's input yet.

   FEATURE: $ARGUMENTS

   DELIBERATION REQUIREMENTS:
   Round 1: Present initial UX assessment for ADHD users and design feasibility
   Round 2: Challenge design assumptions - accessibility, edge cases, micro-interactions
   Round 3: Compare against real-world patterns, consider implementation complexity
   Round 4+: Continue until high confidence

   FOR EACH ROUND:
   - State which round you're in
   - Present new design insights
   - Question assumptions from previous round
   - Consider interaction patterns and user behaviors

   FINAL REPORT:
   - Design recommendation: Build Now/Later/Never (with rationale)
   - UX implications for ADHD users
   - Design effort and feasibility
   - Key design principles applied
   - Interaction specifications (if recommending build)"

2. **Phase 2: Collaborative Discussion Rounds**

   After receiving both independent reports:

   **Discussion Round 1 - Challenge Each Other (Parallel):**
   - Invoke both agents IN PARALLEL
   - PM Prompt: "You've completed independent analysis. Here's Design Lead's analysis: [paste Design output]

   DISCUSSION ROUND 1: Review Design's perspective and respond:
   - What did Design see that you missed?
   - Where do you disagree and why?
   - What questions do you have for Design?
   - Does their analysis change your recommendation?"

   - Design Prompt: "You've completed independent analysis. Here's PM's analysis: [paste PM output]

   DISCUSSION ROUND 1: Review PM's perspective and respond:
   - What did PM see that you missed?
   - Where do you disagree and why?
   - What questions do you have for PM?
   - Does their analysis change your recommendation?"

   **Discussion Round 2 - Refine Through Debate:**
   - If agents still disagree or have unresolved questions, invoke both again IN PARALLEL
   - Each sees the other's Round 1 response
   - Prompt both: "DISCUSSION ROUND 2: Address the questions/concerns raised. Refine your position or explain why you maintain it."

   **Discussion Round 3+ - Converge:**
   - Continue discussion rounds until:
     - Both agents reach consensus (same recommendation), OR
     - Clear trade-offs surface for human decision (can't resolve disagreement)
   - Maximum 3-4 discussion rounds (avoid endless debate)

3. **Phase 3: Consensus Check**

   After discussion rounds, determine outcome:

   **If CONSENSUS (both agree on Build Now/Later/Never):**
   - Proceed to Decision Execution (step 4)

   **If DISAGREEMENT PERSISTS:**
   - Summarize both positions clearly for human
   - Present trade-offs: "PM recommends [X] because [reasons]. Design recommends [Y] because [reasons]."
   - Ask human to decide, then proceed to Decision Execution

4. **Decision Execution**
   - If **Build Now/Later**:
     - Have PM update requirements docs (they know where)
     - Have design lead update design specs (they know where)
     - Create task in `/codebase/chrome-extension/docs/tasks.md` with context from both agents
   - If **Don't Build**:
     - Call `/pm.doc-decision` to document the decision and rationale

5. **Summary**
   - Present synthesis of the collaborative decision process:
     - Convergence points (where agents agreed)
     - Divergence points (where agents disagreed initially)
     - How discussion refined the decision
     - Final consensus recommendation
   - Include links to updated docs and created task (if applicable)
   - Highlight key insights that emerged from the collaborative discussion
