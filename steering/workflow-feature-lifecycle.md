# Feature Lifecycle Workflow

## When to use
Starting a new feature from scratch — from initial idea through to shipped, documented, and debt-logged.

## The Pipeline

```
① PM (requirements.md)
② Designer (design.md UX section)
③ Developer + DevOps in parallel (design.md Architecture + Operations, tasks.md)
④ Tester (test-plan.md, automation, exploratory)
⑤ Release gate (joint sign-off: Tester + DevOps)
⑥ Close-out (living spec, tech debt register, delivery log)
```

The Delivery Lead gates every handoff. The Talent Manager audits capability gaps before step ③.

## Step-by-step

### 1. Kickoff
- Delivery Lead creates the spec folder: `specs/<feature>/`
- Delivery Lead creates `delivery-log.md`
- Delivery Lead runs context-sufficiency check for the PM
- Delivery Lead prompts the user for any missing context (users, outcome, constraints, timeline)

### 2. Requirements (PM)
- PM produces `requirements.md` with EARS acceptance criteria
- Delivery Lead verifies: testable ACs, success metrics, explicit scope, no vague language
- User approves before handoff to Designer

### 3. UX Design (Designer)
- Designer produces the UX section of `design.md`
- Delivery Lead verifies: all states specified, keyboard behavior, final copy, responsive, accessibility
- User approves before handoff to Developer/DevOps

### 4. Architecture + Operations (Developer + DevOps, parallel)
- Developer adds Architecture section to `design.md`
- DevOps adds Operations section to `design.md`
- Developer produces `tasks.md`
- Talent Manager runs capability audit (`capability-audit.md`)
- Delivery Lead verifies both sections, resolves any gaps
- User approves before implementation begins

### 5. Implementation (Developer)
- Developer works through `tasks.md` task by task
- DevOps builds infrastructure, pipelines, observability in parallel
- Tester builds automation in parallel, aligned to `tasks.md`

### 6. Testing (Tester)
- Tester produces `test-plan.md`
- Tester runs exploratory charters
- Tester walks the release quality bar

### 7. Release gate
- Tester + DevOps jointly sign off
- All ACs have passing tests
- Rollback rehearsed in staging
- Observability live
- No open Sev1/Sev2

### 8. Close-out (Delivery Lead)
- Update `specs/product-spec.md` (living spec) with feature summary
- Log any debt in `specs/tech-debt-register.md`
- Final `delivery-log.md` entry with cycle time, loop-backs, systemic signals
- Flag systemic patterns to Talent Manager

## Key rules
- No phase starts until the previous phase's gate passes
- The user approves every major deliverable before the next phase
- Loop-backs are normal — route them cleanly via the Delivery Lead
- Every handoff is logged in `delivery-log.md`
