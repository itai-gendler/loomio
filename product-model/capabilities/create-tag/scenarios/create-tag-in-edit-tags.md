---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Edit tags and adds a tag with a name and color
  kind: actor
  actor: user
  entities:
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product creates the tag for the whole organization
  kind: product
  actor: user
  entities:
  - entity: tag
    effect: creates
    facts:
    - Name
    - Color
  contexts:
    web:
      place: web::signed-in::group
---

# Create a tag in Edit tags

## Trigger

An admin of the organization prepares categories for its work.

## Outcome

The tag is available across the organization.
