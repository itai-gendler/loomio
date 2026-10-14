---
appliesTo:
- type: entity
  id: vote
  effect: creates
  to: Cast
permits:
- related:
  - verb: casts
    entity: user
  when:
  - entity: user
    fact: Deactivated
    is: false
references:
- kind: code
  role: implementation
  target: app/models/ability/stance.rb
- kind: code
  role: implementation
  target: app/services/stance_service.rb#update
---

# Only the voter replaces their own vote

A change made after 15 minutes or after a reply records a new current vote.
