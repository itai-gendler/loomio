---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/comment_service.rb#undiscard
- kind: code
  role: implementation
  target: app/models/ability/comment.rb
---

# Restore comment

Bring a discarded comment back into the thread.
