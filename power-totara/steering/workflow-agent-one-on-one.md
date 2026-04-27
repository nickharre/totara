# Agent 1:1 Review Workflow

## When to use
When you want to review an individual agent's performance, identify areas for improvement, and create an action plan. Run periodically (after every 2–3 features) or when you notice recurring issues with a specific role.

## How to initiate
Say: "Run a 1:1 with [agent name]" — e.g., "Run a 1:1 with Margaret" or "1:1 review for the Developer."

The Talent Manager (Peter) facilitates the review. If Peter is the subject, the Delivery Lead (Gene) facilitates instead.

## Review structure

### 1. Gather evidence

Before the review, collect:

- **Delivery logs** — scan `delivery-log.md` files from recent features for entries involving this agent. Look for: gate rejections, loop-backs routed to them, triage decisions, handoff quality notes.
- **Feedback log** — check `.kiro/steering/_feedback-log.md` for entries that diagnosed issues to this agent's persona or skill gaps.
- **Spec artifacts** — read the agent's recent deliverables (requirements.md for PM, design.md UX section for Designer, architecture section for Developer, etc.) and note quality patterns.
- **Recurring patterns** — identify any issue class that has appeared more than twice involving this agent.

### 2. Assess performance areas

Evaluate the agent against these dimensions. Rate each as Strong / Adequate / Needs Improvement:

| Dimension | What to look for |
|-----------|-----------------|
| **Deliverable quality** | Does the agent's output consistently meet its own quality bar? Are downstream roles able to start without asking clarifying questions? |
| **Handoff readiness** | Do deliverables pass the fitness gate on first attempt, or do they frequently get rejected with gap lists? |
| **Collaboration** | Does the agent engage well with adjacent roles? Does it push back constructively when needed? Does it stay in its lane? |
| **Scope discipline** | Does the agent resist scope creep? Does it flag out-of-scope items rather than silently absorbing them? |
| **Error handling** | When issues are routed to this agent, are they resolved cleanly? Or do they bounce back or recur? |
| **Learning & adaptation** | Has the agent improved on previously flagged issues? Does it apply lessons from past features? |
| **Communication clarity** | Are the agent's artifacts, questions, and handoff notes clear and specific? Or vague and requiring interpretation? |

### 3. Identify improvement areas

From the assessment, identify 1–3 specific improvement areas. Be concrete:

- ❌ "Margaret should write better code" — too vague
- ✅ "Margaret's architecture sections consistently omit failure modes for external dependencies. The last 3 features all had loop-backs from DevOps flagging missing timeout/retry strategies." — specific, evidenced, actionable

For each improvement area, document:
- **What's happening** — the specific pattern or gap
- **Evidence** — delivery log entries, feedback log entries, or specific artifacts
- **Impact** — what downstream cost this creates (rework, delays, escaped bugs)

### 4. Create an action plan

For each improvement area, propose one or more actions:

| Action type | When to use | Example |
|-------------|-------------|---------|
| **New skill doc** | Agent lacks knowledge in a specific technology or pattern | Create `skill-retry-strategies.md` covering timeout, backoff, circuit breaker, and fallback patterns |
| **Persona edit** | Agent's operating principles or anti-patterns need updating | Add "Always specify failure modes for every external dependency" to Developer's Architecture checklist |
| **Quality bar addition** | A specific check is missing from the agent's self-review | Add "[ ] Every external dependency has documented timeout, retry, and fallback behavior" to Developer's quality bar |
| **Collaboration protocol update** | A handoff or interaction pattern needs clarifying | Update Developer ↔ DevOps collaboration protocol to require joint failure-mode review before architecture sign-off |
| **Workflow change** | The process itself needs adjusting | Add a "failure mode review" sub-gate between architecture and implementation |
| **Steering file update** | A convention or guide needs new content | Update `workflow-handoff-gates.md` to include failure-mode check in Developer → Tester gate |

### 5. Document the review

Append the review to `.kiro/steering/_feedback-log.md`:

```markdown
## <date> — 1:1 Review: <Agent Name> (<Alias>)
- **Facilitator:** <Talent Manager or Delivery Lead>
- **Period reviewed:** <feature names or date range>
- **Assessment summary:**
  - Deliverable quality: <rating>
  - Handoff readiness: <rating>
  - Collaboration: <rating>
  - Scope discipline: <rating>
  - Error handling: <rating>
  - Learning & adaptation: <rating>
  - Communication clarity: <rating>
- **Improvement areas:**
  1. <area> — <evidence summary>
  2. <area> — <evidence summary>
- **Action plan:**
  1. <action type>: <specific change> — Owner: <who implements>
  2. <action type>: <specific change> — Owner: <who implements>
- **Watch for:** <how we'll know the improvements are working>
```

### 6. Implement changes

After the user approves the action plan:

- Author any new skill docs
- Apply persona edits (with before/after diff shown to user)
- Update quality bars, collaboration protocols, or workflows
- Log each change in the feedback log with a reference to this 1:1

### 7. Follow up

At the next 1:1 (or the next relevant feature), check:
- Did the improvement areas actually improve?
- Did the action plan changes have the intended effect?
- Any new patterns emerging?

## Rules

- **Evidence-based, not vibes.** Every improvement area must reference specific artifacts or patterns. "I feel like the Designer could do better" is not a finding.
- **1–3 improvements max.** More than three dilutes focus. Pick the highest-impact items.
- **User approves all persona edits.** The 1:1 can propose changes, but persona modifications require explicit user approval before applying.
- **No blame, only systems.** The question is never "why did the agent fail?" — it's "what systemic change prevents this class of issue?"
- **Celebrate strengths.** Note what's working well, not just what needs fixing. Strong areas should be acknowledged in the review summary.
