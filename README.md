# Totara — Spec-Driven Development Team

Seven AI agents. Structured handoffs. Quality gates at every phase. Totara turns your AI coding assistant into a full development team that takes features from rough idea to production.

**[Website](https://nickharre.github.io/totara/)** · **[GitHub](https://github.com/nickharre/totara)**

## What is Totara?

Totara is a multi-agent team system for spec-driven software development. It provides seven specialized agents — Product Manager, UI/UX Designer, Fullstack Developer, DevOps Engineer, Tester, Delivery Lead, and Talent Manager — that collaborate through structured handoffs, fitness gates, and living documentation.

## Available for

### Kiro (Power)

Install as a [Kiro Power](https://kiro.dev/docs/powers/):

1. Open Kiro → Powers panel → "Add power from GitHub"
2. Paste: `https://github.com/nickharre/totara`
3. Totara activates when you mention keywords like "requirements," "design," or "triage"

The Kiro version lives in [`power-totara/`](./power-totara/).

### Claude Code

Copy the Claude Code configuration into your project:

```bash
git clone https://github.com/nickharre/totara.git
cp -r totara/claude-code/.claude your-project/.claude
```

Then open Claude Code and invoke roles with "act as Gene" or "act as Marty."

The Claude Code version lives in [`claude-code/`](./claude-code/).

## The Team

| Agent | Alias | Role |
|-------|-------|------|
| Product Manager | Marty | Owns the "what" and "why." Produces requirements in EARS notation. |
| UI/UX Designer | Dieter | Owns user flows, interaction design, visual design, accessibility. |
| Fullstack Developer | Margaret | Stack-agnostic. Owns architecture and implementation. |
| DevOps Engineer | Charity | Cloud-agnostic. Owns infra, CI/CD, observability, security, cost. |
| Tester | James | Owns test strategy, automation, exploratory testing, release validation. |
| Delivery Lead | Gene | Meta-agent. Gates handoffs, triages issues, maintains delivery log. |
| Talent Manager | Peter | Meta-agent. Audits capability, fills gaps, tunes the team from feedback. |

## The Pipeline

```
① Requirements (Marty) → ② UX Design (Dieter) → ③ Architecture (Margaret + Charity)
→ ④ Implementation (Margaret) → ⑤ Testing (James) → ⑥ Release (joint sign-off)

Gene (Delivery Lead) gates every handoff
Peter (Talent Manager) audits capabilities before implementation
```

## Usage

### Start a new feature

Say: "Start a new feature called user-authentication" — Gene (Delivery Lead) will create the spec folder, check context sufficiency, and kick off the pipeline with Marty (PM).

### Invoke a specific agent

Address agents by name or alias:
- "Marty, write requirements for a payment flow"
- "Dieter, design the onboarding screens"
- "Margaret, architect the notification service"
- "James, write a test plan for the export feature"

In Claude Code, use: "Act as Margaret and architect the auth module."

### Triage an issue

Say: "Triage this bug: checkout returns 500 when cart is empty" — Gene will diagnose the root cause, classify it, and route it to the right agent.

### Run a 1:1 review with an agent

Say: "Run a 1:1 with Margaret" — Peter (Talent Manager) will review the agent's recent performance across seven dimensions, identify 1–3 improvement areas with evidence, and propose an action plan (new skill docs, persona edits, quality bar changes, etc.). Use this after every 2–3 features or when you notice recurring issues with a role.

### Review a handoff

Say: "Review the handoff from Dieter to Margaret" — Gene will check the design deliverable against the Developer's gate requirements and either approve or list specific gaps.

### Run a periodic audit

Say: "Run a periodic review" — this triggers a tech debt review, steering file audit, and living spec check.

## Workflows

| Workflow | Trigger | Guide |
|----------|---------|-------|
| Feature lifecycle | Starting a new feature | `workflow-feature-lifecycle.md` |
| Issue triage | Bug or concern raised | `workflow-triage.md` |
| Handoff gates | Reviewing a deliverable | `workflow-handoff-gates.md` |
| Agent 1:1 review | Performance review of an agent | `workflow-agent-one-on-one.md` |
| Periodic review | Monthly or every 3 features | `guide-periodic-review.md` |
| Team overview | Onboarding someone new | `guide-team-overview.md` |

## License

MIT
