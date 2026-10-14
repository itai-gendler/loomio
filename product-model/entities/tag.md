---
references:
- kind: code
  role: implementation
  target: app/models/tag.rb
- kind: code
  role: implementation
  target: app/services/tag_service.rb
- kind: code
  role: implementation
  target: app/models/ability/tag.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/tags/index.md
---

# Tag

A category tag an organization applies to its threads and polls. Tags belong to the top-level group and are shared by its subgroups.

## Information kept

- **Name** — the tag's name, unique within the organization
- **Color** — the color shown beside the tag
