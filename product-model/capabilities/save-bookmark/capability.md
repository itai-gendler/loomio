---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/bookmark_service.rb#update
- kind: code
  role: implementation
  target: app/models/ability/bookmark.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/users/bookmarks/index.md
---

# Save bookmark

Save a discussion, comment, poll, vote or outcome to one's private Bookmarks.
