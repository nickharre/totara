# Living Spec Convention

## Purpose

The living spec (`specs/product-spec.md`) is the single-document view of what the product *is* — not what it will be, not what it was, but what has been built and shipped. It is a summarised, maintained aggregation of individual feature specs.

## Structure

```markdown
# Product Spec: <Product Name>

> Last updated: <ISO date>
> Maintained by: Delivery Lead

## Product Overview
<2–3 paragraphs: what this product is, who it serves, what outcomes it drives.>

## Feature Index

| Feature | Status | Owner | Spec Folder | Added |
|---------|--------|-------|-------------|-------|
| <name> | shipped / in-progress / planned | <PM who scoped it> | `specs/<feature>/` | <date> |

---

## <Feature Name>

### Summary
<1–2 paragraphs distilled from requirements.md.>

### Key Decisions
<3–5 bullets from design.md.>

### Acceptance Criteria (Summary)
<Top-level EARS criteria, condensed. Link to full spec for detail.>

### Known Limitations & Deferred Scope
<What was explicitly cut.>

### Refs
- Full spec: `specs/<feature>/requirements.md`
- Design: `specs/<feature>/design.md`
- Delivery log: `specs/<feature>/delivery-log.md`
```

## Rules

- **Summarise, don't duplicate.** The living spec is a digest.
- **Update on feature completion.** Not before — reflects what *is*, not what's in progress.
- **In-progress features get an index entry only.** No summary section until shipped.
- **Reflect reality.** If shipped behavior changes, update the living spec.
- **Keep it scannable.** Each feature section readable in under 2 minutes.
- **Product Overview evolves** as features ship.

## Ownership

- **Maintained by:** Delivery Lead (at feature close-out).
- **Reviewed by:** Product Manager (for accuracy).
- **Consumed by:** Everyone.
