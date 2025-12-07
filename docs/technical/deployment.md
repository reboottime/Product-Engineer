# Deployment Strategy

**Status:** Active
**Last Updated:** 2025-12-06

## Overview

Deployment strategy adapts to project phase (defined in `CLAUDE.md` line 7). Each phase balances speed, stability, and risk differently.

---

## Phase-Specific Deployment

### Customer Discovery

**Strategy:** No deployment (research phase)

**Activities:**
- Document findings, not code
- Prototype ideas in design tools
- Validate assumptions with customers
- No production systems yet

**Deliverables:**
- Customer interview notes
- Problem/solution validation
- Market research
- Assumptions documented

---

### POC (Proof of Concept)

**Strategy:** Manual, ad-hoc deployment

**When to deploy:**
- When ready to test technical feasibility
- When validating a specific approach
- No formal schedule

**Process:**
1. Commit to main (auto-pushed)
2. Deploy manually when needed
3. Test the hypothesis
4. Document what worked/didn't work

**Checklist:**
- [ ] Core functionality works
- [ ] Technical approach validated
- [ ] Breaking changes documented

**Monitoring:** Basic error checking, no formal monitoring required

**Rollback:** Not critical (no users yet), but keep previous version accessible

---

### MVP

**Strategy:** Continuous deployment with safety nets

**When to deploy:**
- Auto-deploy on merge to main (if CI configured)
- After PR approval
- During low-traffic windows for major changes

**Process:**
1. Create feature branch
2. Open PR with test plan
3. Review and approve
4. Merge to main
5. Auto-deploy (if configured) or manual deploy
6. Monitor for errors post-deploy

**Checklist:**
- [ ] PR approved
- [ ] Tests pass locally
- [ ] TypeScript builds without errors
- [ ] No console errors in testing
- [ ] Changes tested in target environments

**Monitoring:**
- Check error logs post-deploy (15-30 min)
- User feedback channels monitored
- Basic analytics to detect issues

**Rollback:**
- Keep previous version ready
- Document how to revert (usually: revert commit + redeploy)
- Rollback time target: < 30 minutes

---

### Production

**Strategy:** Staged rollout with comprehensive monitoring

**When to deploy:**
- During scheduled deployment windows
- After staging validation
- With rollback plan documented
- Team available for monitoring

**Process:**
1. Feature branch → PR with enhanced template
2. PR review (consider: require approval)
3. Merge to main
4. Deploy to **staging environment**
5. Run smoke tests in staging
6. Deploy to production (gradual rollout if possible)
7. Monitor metrics for anomalies
8. Confirm stability before moving on

**Pre-Deployment Checklist:**
- [ ] PR approved by reviewer
- [ ] All tests pass (unit + integration)
- [ ] Staging deployment successful
- [ ] Smoke tests pass in staging
- [ ] Performance impact assessed
- [ ] Database migrations tested (if applicable)
- [ ] Rollback plan documented
- [ ] Error monitoring configured
- [ ] Team available for post-deploy monitoring

**Post-Deployment Checklist:**
- [ ] Core user flows tested in production
- [ ] Error rates normal (< baseline + 5%)
- [ ] Performance metrics stable
- [ ] No spike in user reports
- [ ] Monitoring alerts configured

**Monitoring:**
- Real-time error tracking
- Performance metrics (response times, load)
- User analytics (drop-offs, conversions)
- Server health (CPU, memory, disk)

**Rollback:**
- Documented per-deployment
- Tested in staging
- Rollback time target: < 15 minutes
- Include: Code revert, DB rollback (if needed), cache clear

**Incident Response:**
- On-call rotation (if team size allows)
- Escalation path documented
- Post-mortem for production incidents

---

## Deployment Environments

### POC
**Environments:**
- Development (local)
- Optional: Single test environment

### MVP
**Environments:**
- Development (local)
- Production

**Note:** Staging optional but recommended if budget allows

### Production
**Environments:**
- Development (local)
- Staging (required - production mirror)
- Production

**Staging requirements:**
- Matches production configuration
- Uses production-like data (anonymized)
- Accessible for testing before prod deploy

---

## CI/CD Configuration

### POC
**CI/CD:** Not required

Manual deployment is fine. Focus on validating ideas, not automation.

### MVP
**CI/CD:** Recommended (optional)

**Benefits:**
- Auto-run tests on PR
- Auto-deploy on merge (with manual gate)
- Catch errors before production

**Suggested tools:**
- GitHub Actions (simple, free tier)
- Vercel/Netlify (frontend auto-deploy)

**Minimal pipeline:**
```yaml
# Example: .github/workflows/ci.yml
on: [pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm install
      - run: npm test
      - run: npm run build
```

### Production
**CI/CD:** Required

**Pipeline stages:**
1. **Test:** Unit + integration tests
2. **Build:** Compile/bundle application
3. **Deploy Staging:** Auto-deploy to staging on main merge
4. **Smoke Tests:** Automated checks in staging
5. **Deploy Production:** Manual approval gate
6. **Monitor:** Post-deploy health checks

**Required checks:**
- All tests pass
- Build succeeds
- No security vulnerabilities (dependency scan)
- Code coverage maintained (if tracked)

---

## Current Phase Deployment

**Check `CLAUDE.md` line 7 for current phase.**

When phase changes, update:
1. Deployment process (manual → automated → staged)
2. Monitoring requirements
3. Rollback procedures
4. Team responsibilities

---

## Emergency Procedures

### Hotfix Deployment (Production)

**When to use:**
- Critical bug affecting users
- Security vulnerability discovered
- Data integrity issue

**Fast-track process:**
1. Create `hotfix/description` branch
2. Make minimal fix
3. Get expedited review (can be post-deploy if critical)
4. Deploy immediately to production
5. Create PR for documentation (can merge after deploy)
6. Communicate to team

**Post-hotfix:**
- Document what happened
- Create follow-up tasks to prevent recurrence
- Update monitoring to catch similar issues

---

## Notes

**This is a living document.** Update as deployment practices evolve and as you transition between phases.

**Key principle:** Match deployment rigor to project maturity and user risk.