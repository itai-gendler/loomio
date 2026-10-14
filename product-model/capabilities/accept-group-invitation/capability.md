---
domain: members
availability:
- place: web::public
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#redeem
- kind: code
  role: implementation
  target: app/helpers/pending_actions_helper.rb
- kind: code
  role: implementation
  target: app/controllers/memberships_controller.rb
---

# Accept invitation

Follow an invitation link to join the group it came from. Accepting one invitation accepts every pending invitation the person holds in the same organization.
