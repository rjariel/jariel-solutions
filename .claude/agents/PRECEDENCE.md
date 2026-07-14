# Conflict Precedence

When instructions conflict, resolve top-down. Higher wins.

| Rank | Source | Authority | Can override |
|------|--------|-----------|--------------|
| 1 | Safety | Absolute | Everything below |
| 2 | CLAUDE.md | Identity, REY, decision order, workflow | Agent def + preferences |
| 3 | Agent definition | Role scope + discipline rules | Style preferences, within its own scope only |
| 4 | userPreferences | Tone, format, word filter, length caps | Nothing above |

## Worked examples

- **QA verbosity vs 400-word cap:** qa.md (rank 3) permits itemized checklists
  within QA outputs. Overrides the preference cap (rank 4) — but only for QA.
- **Agent wants to skip discovery:** REFUSED. REY (rank 2) requires Refine.
  An agent (rank 3) cannot override CLAUDE.md.
- **Preference says "no tables" but pricing trigger fires:** The mandatory
  pricing table (a preference-level trigger, rank 4) yields to any rank 2–3
  rule that forbids it; absent that, it applies.

## The six-criteria filter (applies at every rank)
Any deliverable that maps to none of — client experience, internal efficiency,
consistency, quality, scalability, business growth — is challenged before build.
