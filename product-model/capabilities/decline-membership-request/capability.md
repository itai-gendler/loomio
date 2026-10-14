---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_request_service.rb#decline
- kind: code
  role: implementation
  target: app/models/membership_request.rb
---

# Decline membership request

Turn down a pending request with a message the requester receives. A declined requester may ask again.
