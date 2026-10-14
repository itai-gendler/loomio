---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/tag_service.rb#update
- kind: code
  role: implementation
  target: app/models/ability/tag.rb
---

# Edit tag

Rename or recolor a tag everywhere in the organization.
