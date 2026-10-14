---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/comment_service.rb#destroy
- kind: code
  role: implementation
  target: app/models/ability/comment.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/comments/index.md
---

# Delete comment

Permanently delete a discarded comment.
