---
availability:
- place: web::signed-in
- place: api
- place: email
references:
- kind: code
  role: implementation
  target: app/services/comment_service.rb#create
- kind: code
  role: implementation
  target: app/models/ability/comment.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/comments/index.md
- kind: code
  role: implementation
  target: app/controllers/api/b2/comments_controller.rb
- kind: code
  role: implementation
  target: app/services/received_email_service.rb#create_comment_from_email
- kind: code
  role: implementation
  target: app/services/task_service.rb
---

# Post comment

Add a comment to a thread, or reply to a discussion, comment, poll, vote or outcome. People mentioned are notified.
