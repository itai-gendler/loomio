---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/tag_service.rb#create
- kind: code
  role: implementation
  target: app/services/tag_service.rb#can_create_tag?
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/tags/index.md
---

# Create tag

Create a new tag for an organization, either from Edit tags or by typing a new name while tagging a thread or poll.
