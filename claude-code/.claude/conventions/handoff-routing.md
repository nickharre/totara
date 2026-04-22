# Handoff & Routing Convention

The team's shared routing rulebook. When an issue is raised or a handoff is imminent, this is the first reference.

## Forward Handoff Chain

```
User → Product Manager → UI/UX Designer ┐
                                         ├→ (Developer + DevOps in parallel) → Tester → Release
                                         ┘
```

The Delivery Lead gates each handoff. Developer and DevOps operate in parallel after the Designer's handoff.

## Per-Handoff Fitness Gates

| From → To | Gate |
|---|---|
| User → PM | Context-sufficiency checklist answered (users, outcome, envelope, constraints). |
| PM → Designer | `requirements.md`: EARS ACs per story; success metrics; explicit scope; UX constraints flagged. |
| PM → Developer/DevOps | As above + NFRs named (availability, latency, data sensitivity, compliance, cost). |
| Designer → Developer | `design.md` UX section: all states per screen; keyboard behavior; final copy; responsive; accessibility. |
| Developer (arch) → Developer (impl) | Architecture section complete; `tasks.md` exists with refs. |
| DevOps → Pre-release | SLO dashboards live; alerts tested; rollback rehearsed; security scans clean; cost alerts wired. |
| Developer → Tester | Tasks complete with passing tests; feature reachable in staging; known-gap list declared. |
| Tester → Release | Every AC has passing test; every design state exercised; a11y + perf pass; no Sev1/Sev2; rollback rehearsed. |

## Issue Triage Taxonomy

Route by **root cause**, not symptom. Assign one **accountable** role; invoke others as supporting.

| Symptom / Issue Type | Primary Owner | Supporting | Notes |
|---|---|---|---|
| Requirement ambiguous or untestable | PM | — | Fix `requirements.md` first |
| Missing UI state (loading/empty/error) | Designer | Developer | Designer specs → Dev implements → Tester verifies |
| Generic or off-brand error copy | Designer | Developer | Do not let Developer improvise copy |
| Flow or navigation gap | Designer | Developer | |
| Visual regression | Designer | Developer | |
| Accessibility — missing from spec | Designer | Developer | Design gap |
| Accessibility — spec'd but not implemented | Developer | Designer (review) | Implementation gap |
| Business-logic bug | Developer | — | |
| Input validation failure | Developer | — | |
| API contract / schema mismatch | Developer | DevOps (if cross-service) | |
| Happy-path performance regression | Developer | DevOps (if env-dependent) | |
| Load / scale performance issue | DevOps | Developer | |
| Availability / reliability / outage | DevOps | Developer | |
| Deployment / rollback / flag issue | DevOps | Developer | |
| Cost surprise | DevOps | Developer (if workload-driven) | |
| Observability gap | DevOps | Developer (if instrumentation needed) | |
| Security — input validation, XSS, injection | Developer | DevOps (WAF/IAM) | |
| Security — secrets, IAM, network, supply chain | DevOps | Developer | |
| Flaky automated test | Tester | Developer (if app race) | |
| Missing test coverage | Tester | — | |
| Recurring bug class, handoff friction | Talent Manager | — | |
| Unclear root cause | Delivery Lead | — | Diagnose before routing |

## Routing Heuristics

When the table doesn't match cleanly:

- **What artifact must change?** Words → Designer. Pixels/states/flows → Designer. Code → Developer. Infra/pipeline/IAM → DevOps. AC → PM. Test → Tester.
- **Could a disciplined version of role X have prevented this?** That role owns it. If multiple, the one earliest in the chain.
- **Does fixing the code leave the design underspecified?** Route to Designer first, then Developer.
- **One-off or pattern?** Pattern → Talent Manager gets a notice.
- **Does this change user-visible behavior in requirements?** PM must sign off.

## Loop-back Patterns

- **Backtrack-one.** Role N−1 fixes alone; forward to N for re-verification.
- **Backtrack-multi.** Must pass through N−1, N−2 before returning.
- **Branch.** Two independent causes; route in parallel; merge for joint re-verification.
- **Spec bug.** Requirements ambiguity. PM fixes spec; downstream may need partial re-do.
- **Cross-cutting escalation.** Systemic gap. Route immediate fix + flag to Talent Manager.

## When to Involve the User

The user decides: scope changes, prioritization, success metrics, MVP line, kill criteria, business constraints, risk posture, preference calls.

The user does NOT decide: which agent fixes a bug, whether a deliverable meets the gate, whether a handoff is ready, how to instrument/test/architect.
