---
appliesTo:
- type: entity
  id: group-follow
  effect: creates
permits:
- related:
  - verb: follows-with
    entity: user
  when:
  - entity: group
    fact: Privacy
    is: Open
  - entity: user
    fact: Email verified
    is: true
references:
- kind: code
  role: implementation
  target: app/models/ability/group.rb
---

# Verified people follow only Open groups they do not belong to

Following ends when the person joins the group.
