---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/reaction_service.rb#update
- kind: code
  role: implementation
  target: app/models/ability/reaction.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/comments/index.md
---

# React

Respond to a discussion, comment, poll, vote or outcome with an emoji. The author is notified in Loomio, not by email.
