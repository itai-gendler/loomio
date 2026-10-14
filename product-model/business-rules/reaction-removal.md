---
appliesTo:
- type: entity
  id: reaction
  effect: removes
permits:
- related:
  - verb: adds
    entity: user
references:
- kind: code
  role: implementation
  target: app/models/ability/reaction.rb
---

# People remove only their own reaction

Removing a reaction affects nobody else's.
