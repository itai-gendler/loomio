---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#remove_admin
- kind: code
  role: implementation
  target: app/models/ability/membership.rb
---

# Demote admin

Take the admin role away from someone, leaving them an ordinary member.
