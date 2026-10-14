---
kind: configuration
of: capability
settings:
- entity: group
  fact: How people join
takesEffect: 'When someone selects Join group: the group''s setting at that moment decides whether they join at once or send a request. A change applies to later attempts.'
stability: Existing members and answered requests are unaffected by a change. A request still pending is dropped when its requester joins after the group starts letting people join without approval.
alternatives:
- id: join-group
  selectedWhen: How people join is Join without approval. Admins of a parent group may also join its subgroups that are not secret, whatever the subgroup's setting.
- id: request-membership
  selectedWhen: How people join is Request to join, which new groups start with. While it is Invitation only, neither is offered and people join only by invitation or a shared link.
references:
- kind: code
  role: implementation
  target: app/models/concerns/group_privacy.rb
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: code
  role: implementation
  target: app/models/ability/membership_request.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/privacy.md
---

# How people join a group

Groups choose whether people join by themselves or ask and wait for approval; both ways of joining are supported side by side across groups.
