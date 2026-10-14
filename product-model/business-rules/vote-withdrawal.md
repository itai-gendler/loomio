---
appliesTo:
- type: entity
  id: vote
  effect: changes
  to: Superseded
permits:
- related:
  - verb: casts
    entity: user
references:
- kind: code
  role: implementation
  target: app/models/ability/stance.rb
- kind: code
  role: implementation
  target: app/services/stance_service.rb#uncast
---

# Only the voter changes or removes their own vote, leaving the earlier one in the history

The earlier vote stays visible in the vote's history.
