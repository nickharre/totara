# Periodic Review Guide

## When to use
Monthly, or after every 3 features shipped, whichever comes first.

## Delivery Lead: Tech Debt Review

Surface the tech debt register (`specs/tech-debt-register.md`) to the PM with:

- New items since last review
- Items whose severity has increased
- Items past their accepted-risk review date
- Recommended paydown candidates for the next cycle

## Talent Manager: Steering Audit (Mode C)

Scan `.kiro/steering/` for:

### Duplication
Two docs covering the same ground → merge or clarify scope.

### Contradiction
Two docs giving conflicting guidance → resolve, don't leave to the reader.

### Orphans
Docs not cited, triggered, or modified in 6 months → candidates for deletion or demotion.

### Inclusion-mode drift
- Files marked `always` that should be `fileMatch` → demote
- Files marked `manual` that are constantly invoked manually → promote to `fileMatch`

### Coverage gaps
Project has grown into tech areas not reflected in steering → propose additions.

### Persona freshness
Personas referring to retired tools, deprecated patterns, or old workflows → prune.

### Feedback-log closure
Items logged but never followed up → close or escalate.

### Deliverable
Produce `_roster-audit-<date>.md` with proposed changes. Apply after user approval.

## Delivery Lead: Living Spec Review

Check `specs/product-spec.md`:
- All shipped features have summary sections
- In-progress features have index entries only
- Product Overview paragraph reflects current scope
- No stale information from changed features
