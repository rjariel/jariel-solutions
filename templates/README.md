# /templates

Reusable document templates. Agents instantiate them; they never invent structure
ad-hoc when a template exists.

## Rules

- Templates are **read-only sources**. Copy to `projects/{client-slug}/{YYYY}/`,
  never edit in place.
- `{{PLACEHOLDER}}` = replace. `____` = fill during the session.
- `<!-- TEMPLATE INSTRUCTIONS -->` blocks are addressed to whoever instantiates
  the template. Delete them in the instance. They are never part of the artifact.
- Sections marked *internal* are stripped before anything reaches a client.
- A template that no longer matches how work actually runs is a defect. Fix the
  template, not the copy.

## Contents

| File | Owner | Used when | Blocks |
|------|-------|-----------|--------|
| `discovery.md` | `business` | Chain entry — before any proposal exists | Everything downstream |
| `proposal-sow.md` | `business` | After `discovery.md` returns GO | Strategy, design, engineering |

## Chain

```
intake → orchestrator (Refine)
       → business: discovery.md → Go/No-Go
       → business: proposal-sow.md → signature
       → brief.md → strategy → design → uiux → dev → qa (gate) → client-success
```

## Success criteria served

| Criterion | How |
|-----------|-----|
| Consistency | Same discovery depth and proposal structure regardless of who runs the call |
| Internal efficiency | No blank-page time; discovery output maps 1:1 onto `brief.md` |
| Quality | Gates catch thin discovery before it becomes underpriced scope |
| Business growth | Explicit go/no-go and change control protect close rate and margin |
