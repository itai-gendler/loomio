---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Delete on the template
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::discussion-templates
- text: The Product deletes the template
  kind: product
  actor: user
  entities:
  - entity: discussion-template
    effect: changes
    from: Visible
    to: Deleted
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-templates
---

# Delete a discussion template

## Trigger

A custom template is no longer needed.

## Outcome

The template is gone from the group.
