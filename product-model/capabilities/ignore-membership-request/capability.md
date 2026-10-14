---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_request_service.rb#ignore
- kind: code
  role: implementation
  target: app/models/membership_request.rb
---

# Ignore membership request

Close a pending request without telling the requester. An ignored request keeps the person from asking again.
