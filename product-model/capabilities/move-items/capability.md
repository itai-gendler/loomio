---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/topic_item_service.rb#move_comments
- kind: code
  role: implementation
  target: app/workers/move_comments_worker.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/moving_items/index.md
---

# Move items

Move selected comments from one thread into another thread, or into a new discussion.
