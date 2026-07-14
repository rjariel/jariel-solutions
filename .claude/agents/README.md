# Jariel Solutions — Agent System

Nine Claude Code subagents that operate the Jariel Solutions business as one
system. Each agent maps to a department; the orchestrator routes; documentation
keeps them consistent. Governed by the root `CLAUDE.md` and filtered through six
success criteria.

## The roster

| Agent | Owns | Chain position |
|-------|------|---------------|
| `orchestrator` | Intake, routing, REY sequencing, handoffs | Entry → routes all |
| `business` | Leads, CRM, discovery, proposals, onboarding, accounts | Chain start |
| `strategy` | Analysis, site strategy, SEO, analytics, AI, CRO | After business |
| `design` | Branding, graphic, marketing assets, identity | Parallel w/ uiux |
| `uiux` | Wireframes, journeys, design systems, a11y, prototypes | Before dev |
| `dev` | WP/Webflow/Framer, custom, API, AI, automation, DevOps | After uiux |
| `qa` | Functional, responsive, a11y, SEO, perf, launch readiness | After dev — the gate |
| `client-success` | Post-launch health, retention, growth, renewals | After launch |
| `documentation` | SOPs, playbooks, standards, knowledge base | Cross-cutting |

Automation/AI is folded into `dev` for now. Split into its own agent when
volume justifies it.

## The value chain

```
user → orchestrator ──► business ──► strategy ──┬──► design ─┐
                                                └──► uiux ◄──┘
                                                       │
                                                       ▼
                                                     dev ──► qa ──► client-success
                                                              │ (fail)
                                                              └──► back to dev

documentation ── serves every agent, at every step
```

## How work moves: the brief

Agents do not chat at each other. They pass a **`brief.md`** — the handoff
contract in `_templates/brief.md`. Every handoff carries an objective,
acceptance criteria, output location, and at least one success criterion. An
incomplete brief is a rejected handoff.

## Conflict resolution

See `PRECEDENCE.md`. Order: Safety → CLAUDE.md → Agent definition →
userPreferences. An agent can override style within its own scope (e.g. QA
checklists), never identity or methodology.

## Success criteria (the filter)

Every deliverable must move at least one: client experience, internal
efficiency, consistency, quality, scalability, business growth. If it moves
none, challenge whether it should be built.

## Files

```
.claude/agents/
├── README.md            ← this file
├── PRECEDENCE.md        ← conflict resolution
├── _templates/
│   └── brief.md         ← the handoff contract
├── orchestrator.md
├── business.md
├── strategy.md
├── design.md
├── uiux.md
├── dev.md
├── qa.md
├── client-success.md
└── documentation.md
```

## Extending

New agent = new `{name}.md` following the shared schema (Role, REY Loop, Scope,
Inputs, Outputs, Handoff, Guardrails). Register its chain position here and its
routing in `orchestrator`. Nothing enters the system without a schema and a
place in the chain.
