# Handoff Gate Verification Workflow

## When to use
A role claims its deliverable is complete and the next role is about to start.

## Gate checks by handoff

### PM → Designer
- [ ] Every user story has testable acceptance criteria in EARS notation
- [ ] Success metrics are named and quantifiable
- [ ] In-scope and out-of-scope are explicit
- [ ] Non-negotiable UX constraints are flagged
- [ ] User has approved the requirements

### PM → Developer/DevOps (for architecture)
- [ ] All of the above, plus:
- [ ] NFRs named: availability, latency, data sensitivity, compliance, cost

### Designer → Developer
- [ ] Every screen has all states: empty, loading, error, success, partial
- [ ] Every interactive element has keyboard behavior specified
- [ ] All copy is final (no placeholders, no Lorem ipsum)
- [ ] Responsive behavior declared for at least two breakpoints
- [ ] Accessibility compliance asserted (WCAG level, contrast, motion)
- [ ] User has approved the design

### Developer (architecture) → Developer (implementation)
- [ ] Architecture section covers: components, data model, API surface, cross-cutting concerns, security review, rollout/rollback
- [ ] `tasks.md` exists with refs to requirements and design
- [ ] Talent Manager capability audit is clear (or gaps acknowledged)

### Developer → Tester
- [ ] Relevant `tasks.md` items complete with passing tests
- [ ] Feature reachable in staging
- [ ] Known-gap list declared (if any)

### DevOps → Pre-release
- [ ] SLO dashboards live
- [ ] Alerts tested (deliberately tripped)
- [ ] Rollback rehearsed in staging within 30 days
- [ ] Security scans clean or accepted with rationale
- [ ] Cost alerts wired

### Tester → Release
- [ ] Every AC has a passing automated test
- [ ] Every design state exercised (automated or exploratory)
- [ ] Accessibility and performance checks pass
- [ ] No open Sev1/Sev2 defects
- [ ] Rollback rehearsed within 30 days

## Procedure

1. Read the current role's quality bar (in their persona file)
2. Read the next role's "When Invoked" section — does the deliverable let them start without guessing?
3. If gate fails: list specific gaps, log in `delivery-log.md`, re-invoke current role
4. If gate passes: present to user for approval with summary + trade-offs + open questions
5. User approves → open gate, log, invoke next role
6. User requests changes → log feedback, re-invoke current role

## Rules
- Rejections are specific, not vibes
- The user always has final say
- If the user says "skip review" or "auto-approve," respect it and log the decision
