---
appliesTo:
- type: entity
  id: subscription
- type: entity
  id: group
- type: entity
  id: thread
- type: entity
  id: poll
- type: entity
  id: comment
references:
- kind: code
  role: implementation
  target: app/models/ability/group_state.rb
- kind: code
  role: implementation
  target: app/models/group.rb#subscription_active?
---

# A group whose plan has lapsed stays readable but accepts no changes

While the organization's plan has lapsed, people can still read the group, its subgroups and their threads, but nobody starts, edits, deletes or moves discussions, comments, polls, votes or outcomes, invites people or changes settings there. Instance administrators are not held back. Members may still change their own Membership details.

## Rationale

A lapsed plan suspends activity without hiding the record the group has built.
