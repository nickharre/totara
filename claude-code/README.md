# Totara for Claude Code

A structured multi-agent development team that runs inside [Claude Code](https://docs.anthropic.com/en/docs/claude-code). Seven specialized roles collaborate through handoffs, quality gates, and living documentation to ship features from idea to production.

This is a port of the [Totara Kiro Power](../power-totara/) adapted for Claude Code's conventions: `CLAUDE.md`, slash commands, and prompt-based role switching.

## The Team

| Alias | Role | Named after | What they own |
|-------|------|-------------|---------------|
| Marty | Product Manager | Marty Cagan | Problem discovery, requirements.md (EARS notation), success metrics, scope |
| Dieter | UI/UX Designer | Dieter Rams | User flows, interaction specs, visual design, accessibility, UX section of design.md |
| Margaret | Fullstack Developer | Margaret Hamilton | Architecture section of design.md, tasks.md, implementation, tests |
| Charity | DevOps Engineer | Charity Majors | Operations section of design.md, CI/CD, infrastructure, observability, security, cost |
| James | Tester | James Bach | Test strategy, test-plan.md, automation, exploratory testing, release gate |
| Gene | Delivery Lead | Gene Kranz | Handoff gating, issue triage, loop-back orchestration, delivery-log.md, living spec, debt register |
| Peter | Talent Manager | Peter Drucker | Capability audits, steering file hygiene, feedback-driven learning, persona edits |

## Quick Start

### 1. Copy into your project

```bash
cp -r claude-code/.claude /path/to/your/project/
mkdir -p /path/to/your/project/specs
```

### 2. Start a feature

Open Claude Code in your project and say:

```
Act as Gene (Delivery Lead). I want to build a feature: <describe your idea>.
```

Gene will:
- Create the spec folder
- Ask you context questions (users, outcomes, constraints)
- Walk you through the pipeline role by role
- Ask for your approval at each handoff

### 3. Switch roles manually

Claude Code doesn't have native multi-agent routing, so you switch roles by prompting:

```
Act as Marty (PM). Read agents/product-manager.md and produce requirements.md for this feature.
```

```
Act as Dieter (Designer). Read agents/ui-ux-designer.md and produce the UX section of design.md.
```

Or let Gene orchestrate — he'll tell you which role to invoke next.

### 4. Load context on demand

Use `/read` to load specific files when needed:

```
/read .claude/agents/delivery-lead.md
/read .claude/conventions/handoff-routing.md
/read .claude/workflows/feature-lifecycle.md
```

## How It Works

### The delivery flow

```
You → Marty (PM) → Dieter (Designer) ┐
                                      ├→ Margaret (Dev) + Charity (DevOps) in parallel → James (Tester) → Release
                                      ┘
```

Gene gates every handoff. Peter audits capabilities before implementation.

### Artifacts produced per feature

```
specs/<feature>/
├── requirements.md        Marty's deliverable
├── design.md              Shared: Dieter (UX) + Margaret (Architecture) + Charity (Operations)
├── tasks.md               Margaret's implementation plan
├── test-plan.md           James's test strategy
├── capability-audit.md    Peter's gap analysis
└── delivery-log.md        Gene's audit trail
```

### Product-level documents

```
specs/
├── product-spec.md        Living spec — product overview of shipped features
└── tech-debt-register.md  Known debt tracker
```

## Directory Structure

```
.claude/
├── CLAUDE.md                          ← Main instructions (loaded automatically)
├── agents/                            ← Role personas (loaded on demand)
│   ├── product-manager.md
│   ├── ui-ux-designer.md
│   ├── fullstack-developer.md
│   ├── devops-engineer.md
│   ├── tester.md
│   ├── delivery-lead.md
│   └── talent-manager.md
├── conventions/                       ← Always-relevant rules
│   ├── handoff-routing.md
│   ├── living-spec.md
│   └── tech-debt-register.md
├── workflows/                         ← On-demand guides
│   ├── feature-lifecycle.md
│   ├── triage.md
│   ├── handoff-gates.md
│   └── periodic-review.md
└── _feedback-log.md                   ← Team learning log
```

## Differences from Kiro

| Capability | Kiro | Claude Code |
|---|---|---|
| Agent invocation | `@Gene` native multi-agent | Prompt: "Act as Gene" + `/read` the persona |
| Always-loaded conventions | `inclusion: always` frontmatter | Referenced in `CLAUDE.md` (auto-loaded) |
| On-demand steering | `inclusion: manual` | `/read` the file when needed |
| Hooks (event-driven automation) | Native hook system | Manual discipline or shell wrappers |
| Gated approvals | Built into handoff flow | Gene asks; you enforce by not proceeding |
| File-match steering | `inclusion: fileMatch` | Not available — load manually when relevant |

## Tips

- **Start with Gene.** He asks the right questions and tells you which role to invoke next.
- **Answer context questions once.** Gene batches them. Give everything at once.
- **Trust the gates.** If Gene blocks a handoff, the gap is real. Fix upstream.
- **Feed Peter.** When something annoys you or recurs, tell Peter. He turns pain into permanent team knowledge.
- **Keep the debt register honest.** Log debt when you create it, not "later."
- **Don't skip the PM.** Marty's discovery phase prevents building the wrong thing.
