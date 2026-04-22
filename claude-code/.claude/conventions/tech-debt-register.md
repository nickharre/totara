# Technical Debt Register Convention

## Purpose

The tech debt register (`specs/tech-debt-register.md`) is the single place where the team records, classifies, and tracks known technical debt. Debt that is not written down is debt that compounds silently.

## Categories

| Category | Examples |
|----------|---------|
| Code | Premature abstraction, duplicated logic, missing validation, hardcoded values |
| Architecture | Tight coupling, missing service boundary, sync that should be async |
| Infrastructure | Manual resource, missing IaC, snowflake config, unrotated secrets |
| Observability | Missing alerts, noisy alerts, missing traces on critical paths |
| Testing | Missing coverage on critical path, flaky tests, no contract tests |
| Security | Known CVE deferred, overly broad IAM role |
| Documentation | Stale runbook, missing API docs, design drift |
| Process | Recurring manual step that should be automated |

## Structure

```markdown
# Technical Debt Register

> Last updated: <ISO date>
> Owned by: Delivery Lead
> Prioritised by: Product Manager

## Summary
- **Total items:** <n>
- **Critical:** <n> | **High:** <n> | **Medium:** <n> | **Low:** <n>
- **Oldest unresolved:** <date> — <title>

---

## <ID>: <Short title>
- **Category:** <code | architecture | infrastructure | observability | testing | security | documentation | process>
- **Severity:** <critical | high | medium | low>
- **Logged:** <ISO date> by <role>
- **Feature origin:** <feature name or "cross-cutting">
- **Description:** <1–3 sentences>
- **Impact if unresolved:** <what gets worse over time>
- **Proposed fix:** <brief — what would resolve it, estimated effort>
- **Blocked by:** <dependency, if any>
- **Status:** open | in-progress | resolved | accepted-risk
- **Resolved:** <ISO date, if resolved> — <how>
```

## Rules

- **Anyone can log debt.** The Delivery Lead ensures it gets into the register.
- **Log at the moment of creation.** Not "when we get around to it."
- **Severity is about compounding cost, not current pain.**
- **The PM prioritises paydown.** Debt competes with feature work.
- **Resolved items stay in the register.** Mark `resolved` with date and method.
- **Accepted risk is valid.** Mark `accepted-risk` with rationale and review date.
- **IDs are sequential.** `TD-001`, `TD-002`, etc.
