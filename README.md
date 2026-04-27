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

## License

MIT
