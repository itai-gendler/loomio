---
appliesTo:
- type: entity
  id: vote
  facts:
  - Reason
- type: capability
  id: cast-vote
references:
- kind: code
  role: implementation
  target: app/models/stance.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/settings/index.md
---

# A vote carries a reason when the poll requires one for the chosen option

Conditional requirements follow the option's icon, so they still apply when Disagree is renamed. A reason needs more than five visible characters, and at most 500 when the poll limits reasons.
