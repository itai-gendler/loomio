---
availability:
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/services/comment_service.rb#update
- kind: code
  role: implementation
  target: app/models/ability/comment.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/comments/index.md
- kind: code
  role: implementation
  target: app/controllers/api/b2/comments_controller.rb
---

# Edit comment

Change a comment. Every edit is kept and anyone who can see the comment can compare versions.
