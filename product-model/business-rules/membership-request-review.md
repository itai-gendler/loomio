---
appliesTo:
- type: entity
  id: membership-request
  effect: changes
permits:
- related:
  - verb: receives
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: membership
    fact: Role
    is: Admin
- related:
  - verb: receives
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: group
    fact: Members can add members
    is: true
references:
- kind: code
  role: implementation
  target: app/models/ability/membership_request.rb
---

# Admins review membership requests, and members do when the group lets them add members

A request is answered once; the answer is final.
