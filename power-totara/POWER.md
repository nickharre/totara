---
name: "totara"
displayName: "Totara — Spec-Driven Development Team"
description: "Seven AI agents with structured handoffs and quality gates to take features from idea to production"
keywords: ["team", "agents", "spec-driven", "requirements", "design", "delivery", "handoff", "product-manager", "designer", "developer", "devops", "tester", "qa", "talent", "tech-debt", "living-spec", "routing", "triage", "totara"]
author: "Nick Harre"
---

# Totara — Spec-Driven Development Team

A complete multi-agent team that turns rough ideas into shipped, tested, documented software through structured handoffs and quality gates. Named after the Tōtara tree — a native New Zealand podocarp that lives over 1,000 years. Like the Tōtara, software built with this team is rooted in craft, built to endure.

## What this power provides

Seven specialized agents, each with a distinct role, operating principles, quality bar, and collaboration protocol:

| Agent | Alias | Role |
|-------|-------|------|
| Product Manager | Marty | Owns the "what" and "why." Produces requirements.md in EARS notation. |
| UI/UX Designer | Dieter | Owns user flows, interaction design, visual design, accessibility. Produces the UX section of design.md. |
| Fullstack Developer | Margaret | Owns architecture and implementation. Drives the architecture section of design.md, produces tasks.md, and implements the feature. |
| DevOps Engineer | Charity | Owns infrastructure, CI/CD, observability, security, reliability, cost. Contributes the Operations section of design.md. |
| Tester | James | Owns test strategy, automation, exploratory testing, and release validation. Produces test-plan.md. |
| Delivery Lead | Gene | Meta-agent. Drives handoffs, gates each phase, triages issues, maintains delivery-log.md. |
| Talent Manager | Peter | Meta-agent. Audits team capability against specs, fills gaps with skill docs, tunes the team from feedback. |

Plus three cross-cutting conventions:
- **Handoff & Routing** — the team's shared playbook for who owns what kind of issue
- **Living Spec** — a single-document product overview aggregating shipped features
- **Tech Debt Register** — tracks known debt across code, architecture, infra, testing, security, docs, and process

## Onboarding

### Step 1: Install agent personas

Copy the agent files from `steering/agents/` into your workspace at `.kiro/agents/`:

```
.kiro/agents/
├── product-manager.md
├── ui-ux-designer.md
├── fullstack-developer.md
├── devops-engineer.md
├── tester.md
├── delivery-lead.md
└── talent-manager.md
```

Each agent is invoked manually via `@` mention or by the Delivery Lead during handoffs.

### Step 2: Install convention steering files

Copy the convention files from `steering/conventions/` into `.kiro/steering/`:

```
.kiro/steering/
├── convention-handoff-routing.md    (inclusion: always)
├── convention-living-spec.md        (inclusion: always)
├── convention-tech-debt-register.md (inclusion: always)
└── _feedback-log.md                 (inclusion: manual)
```

These load automatically and guide all agents on routing, documentation, and debt tracking.

### Step 3: Create the specs directory structure

```
specs/
├── product-spec.md          ← living spec (created by Delivery Lead after first feature ships)
├── tech-debt-register.md    ← debt register (created when first debt is logged)
└── <feature>/               ← one folder per feature
    ├── requirements.md
    ├── design.md
    ├── tasks.md
    ├── test-plan.md
    ├── capability-audit.md
    └── delivery-log.md
```

### Step 4: Add hooks (optional)

Add a hook to run the Talent Manager's capability audit before implementation starts:

```json
{
  "name": "Capability Audit Before Implementation",
  "version": "1.0.0",
  "description": "Run a capability audit when tasks.md is created to catch skill gaps before coding starts",
  "when": {
    "type": "fileCreated",
    "patterns": ["**/specs/**/tasks.md"]
  },
  "then": {
    "type": "askAgent",
    "prompt": "Run a Mode A capability audit on this feature's specs. Check requirements.md, design.md, and tasks.md for any technologies, patterns, or regulations the team isn't equipped for."
  }
}
```

## When to load steering files

- Starting a new feature → `workflow-feature-lifecycle.md`
- Triaging a bug or issue → `workflow-triage.md`
- Reviewing a handoff deliverable → `workflow-handoff-gates.md`
- Running a 1:1 review with an agent → `workflow-agent-one-on-one.md`
- Onboarding a new team member → `guide-team-overview.md`
- Running a periodic audit → `guide-periodic-review.md`
