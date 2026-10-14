---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/tag_service.rb#destroy
---

# Delete tag

Delete a tag, removing it from every thread and poll in the organization.
