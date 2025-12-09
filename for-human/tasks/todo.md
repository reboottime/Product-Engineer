# Todo

See `/for-human/manuals/agentic-system-roadmap.md` for full roadmap.

## High Priority

### Phase 1 Foundation Tasks

- [] Instill the concept that time is irrelevant to Ai team members (product & Engineer & claude itself)
- [ ] Review `/for-human/manuals/agentic-system-team.md` - validate team design matches your mental model
- [x] clean up agent memory design doc
- [] test memory design for agents
  - founding product manager
  - product design lead

### Product Manager Agent

- [ ] generate prd
- [ ] help design product design lead agent
- [ ] on eval
  - [ ] growth pm: then scale from 1~10
    - [ ] pass framework evaluation

### Product Design Lead Agent

- [ ] it can generate spec file
- [ ] it can generate wireframe
- [ ] generate design system

### Release Manager Agent

- [ ] feature commit vs atomic commit to real world engineering practice
- [ ] colloberation between codebase agents

### System Validation

- [ ] Test current agents against team design
  - [ ] Try `/pm.validate-feature` with a sample feature
  - [ ] Try `/design.flow` with a sample feature
  - [ ] Try `/git.add-pr` workflow
  - [ ] Document what works vs gaps
- [ ] Define toy app scope for validation
  - [ ] Choose simple 0-1 problem (solve for yourself)
  - [ ] Write down: problem, target user (you), success metric
  - [ ] Keep it <1 week to build

## Medium Priority

### Memory System

- [ ] Design memory system requirements
  - [ ] What info do agents need to remember? (customer insights, decisions, architecture)
  - [ ] What templates compress knowledge best? (PRD format, wireframe format, spec format)
  - [ ] How to structure `/docs/` for token efficiency?
- [ ] Audit existing `/docs/` structure
  - [ ] What's redundant? (combine or delete)
  - [ ] What's missing? (add placeholders)
  - [ ] What's bloated? (compress using `/sys.optimize-doc`)

## Low Priority

