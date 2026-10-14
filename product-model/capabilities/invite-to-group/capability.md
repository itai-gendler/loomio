---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/group_service.rb#invite
- kind: code
  role: implementation
  target: app/extras/user_inviter.rb
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/inviting_people/index.md
---

# Invite people to group

Invite people to a group by email address, by name, or by choosing a related group of the same organization, optionally into several of its subgroups at once. Each invitee receives a single-use invitation link and counts as a member from the moment they are invited.
