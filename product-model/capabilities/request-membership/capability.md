---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_request_service.rb#create
- kind: code
  role: implementation
  target: app/models/membership_request.rb
- kind: code
  role: implementation
  target: vue/src/components/group/membership_request_form.vue
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/inviting_people/index.md
---

# Request to join

Ask to join a group that requires approval, answering its joining prompt. The group's admins are notified.
