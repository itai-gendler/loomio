---
appliesTo:
- type: entity
  id: reaction
  effect: changes
permits:
- related:
  - verb: adds
    entity: user
references:
- kind: code
  role: implementation
  target: app/models/ability/reaction.rb
---

# People change only their own reaction

Changing a reaction replaces its emoji.
