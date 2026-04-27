# Issue Triage Workflow

## When to use
A bug, concern, or question has been raised — by the Tester, the user, an automated check, or any agent.

## Procedure

### 1. Gather evidence
- Reproduction steps, screenshots, logs, the spec line it contradicts
- Environment details (browser, OS, build, feature flag state)

### 2. Diagnose root cause (not symptom)
Ask: "What artifact must change to fix this?"

| If the fix is... | Route to... |
|---|---|
| Words (copy, labels, messages) | Designer |
| Pixels/states/flows | Designer → Developer |
| Code (logic, validation, API) | Developer |
| Infrastructure/pipeline/IAM/observability | DevOps |
| Acceptance criteria | PM |
| Test coverage | Tester |

### 3. Apply routing heuristics
- Could a disciplined version of role X have prevented this? → That role owns it
- Does fixing the code leave the design underspecified? → Designer first, then Developer
- Is this a one-off or a pattern? → Pattern → flag to Talent Manager
- Does this change user-visible behavior in requirements? → PM must sign off

### 4. Route with a specific action request
Write a triage note: symptom, root-cause hypothesis, the AC or design statement it violates, what needs to change.

### 5. Sequence multi-role fixes
If the fix requires Designer → Developer → Tester:
- Open a loop-back record in `delivery-log.md`
- Hand each role a specific request
- Update the record after each step
- Close when verified

### 6. Log everything
- Triage record in `delivery-log.md`
- If the same class of issue recurs 3+ times → flag to Talent Manager as systemic

## Common routing examples

| Issue | Primary | Supporting |
|---|---|---|
| Generic 404 page, no brand | Designer | Developer |
| API 500 on trailing whitespace | Developer | Tester |
| Checkout latency spike after deploy | DevOps | Developer |
| Ambiguous acceptance criterion | PM | — |
| Screen reader announces "button" with no label | Developer | Designer (if label wasn't specified) |
| Intermittent 403 on auth'd requests | Developer | DevOps |

## Anti-patterns
- Routing on symptom instead of cause
- Bouncing triage decisions to the user
- Split-blaming across multiple roles
- Ping-pong routing without re-diagnosis
