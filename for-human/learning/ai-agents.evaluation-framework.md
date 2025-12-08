# AI Agent Evaluation Framework

Systematic checklist for evaluating custom agents before deployment. Use this when creating new agents or refining existing ones.

---

## 1. Context Alignment

**Does the agent fit the work it's designed for?**

- [ ] Phase coverage matches intended use (Discovery/POC/MVP/Production)
- [ ] Thinking model fits work type (hypothesis-driven vs metrics-driven vs execution-focused)
- [ ] Scope boundary appropriate (product vs engineering vs design)
- [ ] Complements human strengths/weaknesses (doesn't duplicate what human does well)
- [ ] Role identity clear and consistent throughout prompt

**Red flags:**

- Agent tries to do everything (no clear boundaries)
- Thinking model conflicts with phase (e.g., perfectionist in 0→1)
- Overlaps with human's strongest skills

---

## 2. Input/Output Clarity

**Does the agent know where to get info and where to put results?**

- [ ] Input sources explicitly listed (files/folders it reads)
- [ ] Output destinations specified (where it writes)
- [ ] File/folder dependencies documented
- [ ] Expected structure defined (templates, formats)
- [ ] First-spawn instructions clear (what to read first)

**Red flags:**

- Agent assumes files exist without checking
- Output location ambiguous
- No guidance on what to read on first run
- Undefined file formats

**Test:** Can agent find all inputs in a fresh project? Do outputs have clear homes?

---

## 3. Decision Authority

**Is it clear what agent decides vs escalates?**

- [ ] Autonomous decisions listed (what agent does without asking)
- [ ] Consultation triggers defined (when to ask human)
- [ ] Escalation criteria specified (when to stop and alert)
- [ ] Authority level appropriate for role (founding PM ≠ growth PM)
- [ ] Balances speed (autonomy) with risk (escalation)

**Red flags:**

- Everything requires approval (too slow)
- No escalation criteria (too risky)
- Decides on things outside expertise
- Unclear when to ask vs decide

**Test:** Agent encounters ambiguous requirement - does it know whether to decide or ask?

---

## 4. Template Portability

**Can this agent work across different projects?**

- [ ] No project-specific assumptions baked in
- [ ] Works with placeholder/empty strategy docs
- [ ] Adapts to different industries/contexts
- [ ] First-spawn adapts to new project (reads context, adjusts)
- [ ] Generic workflows (not hardcoded to one product)

**Red flags:**

- References specific product features in prompt
- Assumes particular tech stack
- Industry-specific without flexibility
- Hardcoded file names or paths unique to one project

**Test:** Drop agent into unrelated project - does it still function?

---

## 5. Integration

**Does it work well with the system and other agents?**

- [ ] Follows CLAUDE.md communication rules (concise, structured, no preambles)
- [ ] Uses correct tools (TodoWrite, AskUserQuestion, Read/Edit/Write)
- [ ] Coordinates with other agents (clear handoff points)
- [ ] Shared folder usage defined (who writes where)
- [ ] Respects git conventions and commit guidelines
- [ ] No tool usage anti-patterns (echo for communication, unnecessary bash)

**Red flags:**

- Violates communication style (long prose, preambles)
- Agent-to-agent conflicts (both write same file)
- Uses wrong tools (bash cat instead of Read)
- Unclear handoffs between agents

**Test:** Run agent alongside other agents - any conflicts or coordination issues?

---

## 6. Human Understanding

**Does human know how to work with this agent?**

- [ ] When to use agent documented (use cases clear)
- [ ] When NOT to use agent documented (anti-patterns)
- [ ] Artifacts explained (why each folder/file exists)
- [ ] Workflow guide exists (`/for-human/learning/[agent]-workflow.md`)
- [ ] Example flows shown (real scenarios)
- [ ] Human's role defined (what they do vs agent does)

**Red flags:**

- No documentation for humans
- Artifacts unexplained (mysterious folders)
- No examples of real usage
- Unclear when to spawn agent

**Test:** New team member reads docs - can they use agent effectively?

---

## 7. Failure Modes

**How does agent handle problems gracefully?**

- [ ] Missing file strategy (create, prompt human, or fail gracefully)
- [ ] Incomplete input handling (asks for clarification vs assumes)
- [ ] Conflict resolution defined (what if requirements contradict)
- [ ] Recovery from bad decisions (can it backtrack)
- [ ] Error messages helpful (not just "file not found")

**Red flags:**

- Hard failures on missing files
- Assumes input is complete/correct
- No recovery mechanism
- Continues with bad assumptions

**Test:** Remove expected file - does agent fail gracefully or crash?

---

## 8. Workflow Completeness

**Are all critical paths covered?**

- [ ] Happy path defined (standard workflow start to finish)
- [ ] Edge cases handled (what if no users to interview?)
- [ ] Exit conditions clear (when to stop, hand off, kill)
- [ ] Transition points defined (to next phase/agent)
- [ ] Iterative loops specified (how to repeat parts of workflow)
- [ ] Kill criteria defined (when to abandon approach)

**Red flags:**

- Only happy path covered
- No exit strategy
- Unclear when workflow is "done"
- Missing transition/handoff steps
- No guidance on iterations

**Test:** Workflow hits edge case - does agent know what to do?

---

## 9. Success Metrics

**How do you measure if agent is working well?**

- [ ] Output quality measurable (validated hypotheses, shipped features, etc.)
- [ ] Efficiency trackable (time saved, decisions made)
- [ ] Human satisfaction indicators (fewer questions, clearer outputs)
- [ ] Refinement triggers defined (what indicates agent needs improvement)
- [ ] Value metrics specified (business/product outcomes)

**Red flags:**

- No way to measure effectiveness
- Only activity metrics (not outcomes)
- Can't tell good performance from bad
- No feedback loop for improvement

**Test:** After using agent 10 times - can you tell if it's working well?

---

## 10. Conflict Prevention

**Does agent avoid stepping on toes?**

- [ ] File ownership clear (who writes what)
- [ ] Concurrent usage safe (multiple agents don't conflict)
- [ ] Version control strategy (how changes are tracked)
- [ ] Override rules defined (human vs agent edits)
- [ ] Coordination protocol (how agents share info)

**Red flags:**

- Multiple agents write same file
- No ownership boundaries
- Agent overwrites human edits
- Unclear who has authority on conflicts

**Test:** Two agents run simultaneously - any file conflicts or confusion?

---

## 11. Efficiency

**Does agent use resources wisely?**

- [ ] Minimizes token usage (concise, targeted reads)
- [ ] Avoids redundant file operations (caches context)
- [ ] Uses parallel tool calls when possible
- [ ] Creates only necessary artifacts (no bloat)
- [ ] Targeted searches (doesn't read everything)

**Red flags:**

- Reads entire codebase for simple query
- Creates redundant files
- Sequential when could be parallel
- Token-heavy outputs with no value

**Test:** Track token usage - is it proportional to value delivered?

---

## 12. Adaptability

**Can agent handle variety?**

- [ ] Works across industries (SaaS, consumer, B2B, etc.)
- [ ] Scales to project size (startup to enterprise)
- [ ] Adapts to human work styles (hands-on vs hands-off)
- [ ] Handles different platforms (web, mobile, extension, API)
- [ ] Flexible on methodology (Lean, Agile, Shape Up, etc.)

**Red flags:**

- Only works for one industry
- Assumes specific company size
- Rigid methodology requirements
- Platform-specific when should be generic

**Test:** Use agent in different context (B2B vs consumer) - still effective?

---

## Evaluation Scores

Rate each dimension: **Pass** / **Needs Work** / **Fail**

### Critical (must pass)

1. Context Alignment: ___
2. Input/Output Clarity: ___
3. Decision Authority: ___
6. Human Understanding: ___
7. Failure Modes: ___

### Important (should pass)

4. Template Portability: ___
5. Integration: ___
8. Workflow Completeness: ___
9. Success Metrics: ___

### Nice-to-have

10. Conflict Prevention: ___
11. Efficiency: ___
12. Adaptability: ___

**Overall:** Ready to deploy / Needs refinement / Back to drawing board

---

## Example: Founding Product Manager Evaluation

**1. Context Alignment:** ✓ Pass

- Phase: Discovery → POC (correct for 0→1)
- Thinking: Hypothesis-driven (appropriate)
- Boundary: Product only, no engineering (clear)

**2. Input/Output Clarity:** ✓ Pass

- Reads: CLAUDE.md, strategy.md, /research/
- Writes: /research/{interviews,insights,learnings,validated}, /requirements/, /metrics/
- All documented in workflow guide

**3. Decision Authority:** ✓ Pass

- Autonomous: Prioritization, scope cuts, research methods
- Consult: Business model pivots, audience shifts
- Escalate: Ethical/legal issues

**6. Human Understanding:** ✓ Pass

- Workflow guide created
- Folder structure explained with Q&A
- Example flows documented

**7. Failure Modes:** ⚠ Needs Work

- Missing strategy.md handling not specified
- Should prompt human to fill template

**Overall:** Ready to deploy (with note to add strategy.md fallback)

---

## Using This Framework

**When creating new agent:**

1. Draft agent prompt
2. Run through checklist
3. Fix gaps before deployment
4. Create human documentation (#6)

**When refining existing agent:**

1. Identify issues (agent asking too much? wrong outputs?)
2. Map to framework dimension
3. Fix specific dimension
4. Re-evaluate

**When deciding between multiple approaches:**

- Score each approach on critical dimensions
- Approach with most "Pass" scores wins
