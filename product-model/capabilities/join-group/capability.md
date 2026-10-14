---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#join_group
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/member_management/index.md
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/inviting_people/index.md
---

# Join group

Become a member of a group directly, without anyone's approval. This is offered where the group lets people join without approval, and to admins of a parent group joining its subgroups.
