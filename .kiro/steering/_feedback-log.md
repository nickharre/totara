---
inclusion: manual
description: Append-only log of team-level learning events, maintained by the Talent Manager. Every entry captures a feedback signal (from the user, a recurring issue, or a production escape), its diagnosis, the change applied, and a watch-for condition.
---

# Team Feedback & Learning Log

This file is the team's institutional memory. The Talent Manager appends one entry per learning event — evidence, diagnosis, change, watch-for.

Do not edit existing entries. To supersede a lesson, write a new entry that references the old one and explains what changed.

## Entry Template

```markdown
## <YYYY-MM-DD> — <short title>
- **Signal:** <verbatim user quote, recurring pattern, or incident reference>
- **Diagnosis:** <category — persona gap | skill gap | convention gap | workflow gap | spec gap | user-preference gap> — <one-line rationale>
- **Change applied:** <file(s) modified or created, scope>
- **Evidence trail:** <commit / session / log link>
- **Watch for:** <how we will know this worked — specifically, what should *not* recur>
```

## Entries

<!-- Append new entries below. Most-recent first. -->

## 2026-04-28 — Marketing site: "no hint of AI slop" — structural overhaul required
- **Signal:** User: "I need this to look exceptional. Clean, clear with no hint of AI slop."
- **Diagnosis:** skill gap — Dieter's initial design used template patterns (3×2 card grids, centered everything, uniform section padding, Lucide icon grids) that read as AI-generated. Three review cycles were needed before the layout felt hand-crafted.
- **Change applied:** Major structural overhaul of `docs/index.html` — replaced feature card grid with numbered list, replaced agent card grid with compact roster, left-aligned hero, varied section padding, added dark green CTA background, removed SVG icons from features/agents.
- **Evidence trail:** This conversation session, multiple Dieter review cycles.
- **Watch for:** Future marketing/landing page work should avoid card grids as the default layout. Dieter should propose at least two distinct visual structures per page, not repeat the same card pattern across sections.

## 2026-04-28 — Marketing site: card grids used twice back-to-back
- **Signal:** Dieter review: "Two consecutive sections of white cards on a warm background with identical styling is the clearest signal that this page was assembled from components, not designed as a whole."
- **Diagnosis:** persona gap — Dieter's initial output defaulted to card grids for both features and agents without recognizing the repetition as a design problem. A designer should catch same-layout-twice-in-a-row before the first review.
- **Change applied:** Features → numbered list layout. Agents → compact roster with warm background. The two sections now have fundamentally different visual structures.
- **Evidence trail:** Dieter's "AI slop" review in this session.
- **Watch for:** Dieter should never produce two adjacent sections with the same layout structure. If a card grid is used once, the next section must use a different format.

## 2026-04-28 — Marketing site: centered hero as default
- **Signal:** Dieter review: "Centered heroes are the #1 template tell."
- **Diagnosis:** persona gap — Dieter's initial hero was centered text with a faint centered background. This is the default AI-generated hero pattern. A left-aligned hero with asymmetric composition is more distinctive.
- **Change applied:** Hero content left-aligned, tree rings SVG repositioned to right bleed, eyebrow changed from italic serif to uppercase mono for contrast.
- **Evidence trail:** Dieter's final review in this session.
- **Watch for:** Future hero sections should default to asymmetric/left-aligned layouts. Centered heroes should require explicit justification.

## 2026-04-28 — Marketing site: uniform section padding
- **Signal:** Dieter review: "Everything is evenly spaced. This is the problem... The page has a metronomic beat."
- **Diagnosis:** skill gap — Margaret applied identical `padding: 100px 0` to every section. A designed page varies padding to create rhythm (compression and expansion).
- **Change applied:** Pipeline 80px, Features 120px, Agents 80px, Install 100px, CTA 80px. No two adjacent sections share the same padding.
- **Evidence trail:** Dieter's rhythm review in this session.
- **Watch for:** Margaret should vary section padding by default when implementing multi-section pages. Same padding on adjacent sections should be flagged as a potential issue.

## 2026-04-28 — Logo PNG color mismatch with CSS accent
- **Signal:** User: "The background of the totara logo is a slightly diff green to the navbar."
- **Diagnosis:** convention gap — No convention existed for ensuring asset colors match CSS tokens. The logo PNG had a baked-in green that didn't match `--accent: #2d5a3d`.
- **Change applied:** User provided transparent PNG (`TotaraLogoTransparent.png`). Favicon and nav brand updated to use it.
- **Evidence trail:** This conversation session.
- **Watch for:** Any raster asset (PNG, JPG) placed on a colored CSS background should use a transparent background. Color matching between assets and CSS tokens should be verified at implementation time.

## 2026-04-28 — ARIA tab pattern without keyboard support
- **Signal:** Dieter review: "Shipping incorrect ARIA is worse than shipping no ARIA."
- **Diagnosis:** skill gap — Margaret implemented `role="tablist"` and `role="tab"` but omitted arrow-key navigation, which the ARIA tabs pattern requires.
- **Change applied:** Added arrow-key (left/right/up/down) navigation to platform tab JS with focus management and tabindex updates.
- **Evidence trail:** Dieter's final review in this session.
- **Watch for:** Any future use of ARIA tab roles must include keyboard navigation. If keyboard support isn't feasible, use simple buttons without ARIA tab roles.

## 2026-04-28 — 1:1 Review: UI/UX Designer (Dieter)
- **Facilitator:** Peter (Talent Manager)
- **Period reviewed:** Marketing site design — Totara landing page (this session)
- **Assessment summary:**
  - Deliverable quality: Adequate → Strong (improved across 3 review cycles)
  - Handoff readiness: Needs Improvement — initial designs required 3 review cycles before being implementation-ready
  - Collaboration: Strong — pushed back constructively on layout choices, gave specific CSS values, worked well with Margaret
  - Scope discipline: Strong — stayed focused on visual design, didn't drift into copy or architecture
  - Error handling: Strong — when issues were flagged (contrast, ARIA, logo mismatch), provided clear, specific fixes
  - Learning & adaptation: Strong — each review cycle was noticeably better than the previous. The final "AI slop" review showed genuine design thinking
  - Communication clarity: Strong — reviews were specific, referenced exact CSS values and line numbers, prioritized findings clearly
- **Strengths to celebrate:**
  - The "AI slop" review was exceptional. Dieter correctly identified that the problem wasn't the palette or typography (which were good) but the *layout structure* — two identical card grids, centered everything, uniform spacing. This is the kind of structural diagnosis that separates a designer from a stylist.
  - Accessibility catches were thorough: contrast ratios, ARIA patterns, focus states, screen reader semantics. These weren't afterthoughts — they were integrated into every review.
  - The final design direction (left-aligned hero, numbered feature list, compact agent roster, dark CTA) is genuinely distinctive. It doesn't look like a template.
- **Improvement areas:**
  1. **Initial output defaults to template patterns.** Dieter's first design pass produced centered hero + 3×2 card grid + 3×2 card grid — the exact layout every AI generator produces. It took the user explicitly asking for "no AI slop" to trigger the structural rethink. A world-class designer should catch this on the first pass, not the third.
     - Evidence: First marketing site version had identical card grids for features and agents, centered hero with faint background, uniform 100px section padding.
     - Impact: 3 full review cycles before the layout was acceptable. Each cycle involved reading the full HTML, producing a review, and implementing changes — significant time cost.
  2. **Contrast and accessibility issues not caught in initial design.** The first version shipped with `--text-muted` failing WCAG AA, nav links at 2.8:1 contrast, and no focus-visible on interactive elements. These should be caught during design, not during review.
     - Evidence: First Dieter review identified these as Critical/High issues — meaning they were present in the design he helped create.
     - Impact: Accessibility fixes had to be retrofitted across every section.
- **Action plan:**
  1. **Persona edit:** Add to Dieter's Anti-patterns: "Template-first design. Defaulting to centered hero + card grids + uniform spacing. Every page should have at least two visually distinct section structures. If you catch yourself using the same card layout twice on one page, stop and redesign one of them." — Owner: Peter (pending user approval)
  2. **Quality bar addition:** Add to Dieter's quality bar: "[ ] No two adjacent sections share the same layout structure (e.g., two card grids back-to-back)." — Owner: Peter (pending user approval)
  3. **Quality bar addition:** Add to Dieter's quality bar: "[ ] All text colors verified against their background at WCAG AA (4.5:1 for normal text, 3:1 for large text) before handoff." — Owner: Peter (pending user approval)
  4. **Quality bar addition:** Add to Dieter's quality bar: "[ ] Section padding varies across the page — no metronomic rhythm." — Owner: Peter (pending user approval)
- **Watch for:** Next marketing or landing page work should produce a non-template layout on the first pass, not the third. Contrast ratios should be verified before the first review, not caught during it.
