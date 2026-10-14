---
domain: discussions
availability:
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/services/topic_service.rb#discard_without_authorization
- kind: code
  role: implementation
  target: app/models/ability/discussion.rb
- kind: code
  role: implementation
  target: app/controllers/api/b2/discussions_controller.rb
---

# Delete discussion

Delete a discussion together with its thread and every poll in it.
