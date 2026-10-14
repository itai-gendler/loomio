---
kind: primary
routes:
  web: Web
steps:
- text: The User changes a tag's name or color in Edit tags
  kind: actor
  actor: user
  entities:
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product updates the tag throughout the organization, merging it into an existing tag of the same name
  kind: product
  actor: user
  entities:
  - entity: tag
    effect: changes
    facts:
    - Name
    - Color
  contexts:
    web:
      place: web::signed-in::group
---

# Edit a tag

## Trigger

An organization admin renames or recolors a tag.

## Outcome

Every thread and poll in the organization shows the new name and color.
