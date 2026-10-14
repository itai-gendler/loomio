---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Delete on a tag in Edit tags
  kind: actor
  actor: user
  entities:
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product deletes the tag and removes it from every thread in the organization
  kind: product
  actor: user
  entities:
  - entity: tag
    effect: removes
  - entity: thread
    effect: changes
    facts:
    - Tags
  contexts:
    web:
      place: web::signed-in::group
---

# Delete a tag

## Trigger

An organization admin removes a category nobody uses.

## Outcome

The tag is gone from every thread and poll in the organization.
