---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_request_service.rb#approve
- kind: code
  role: implementation
  target: app/models/ability/membership_request.rb
---

# Approve membership request

Accept a pending request to join, making the requester a member.
