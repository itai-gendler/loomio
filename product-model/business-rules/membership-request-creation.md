---
appliesTo:
- type: entity
  id: membership-request
  effect: creates
permits:
- related:
  - verb: sends
    entity: user
  when:
  - entity: group
    fact: How people join
    is: Request to join
references:
- kind: code
  role: implementation
  target: app/models/ability/membership_request.rb
- kind: code
  role: implementation
  target: app/models/membership_request.rb
---

# People request to join only groups that require approval

The requester must be able to see the group and not already belong to it. A pending or ignored request keeps them from asking again; a request declined with a message does not.
