---
appliesTo:
- type: entity
  id: membership-request
  effect: removes
permits:
- related:
  - verb: sends
    entity: user
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#join_group
---

# A pending request goes only when its requester joins

Joining a group directly drops the request the person had pending there.
