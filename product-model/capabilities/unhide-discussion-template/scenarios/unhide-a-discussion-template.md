---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Unhide on a hidden template
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::discussion-templates
- text: The Product shows the template again
  kind: product
  actor: user
  entities:
  - entity: discussion-template
    effect: changes
    from: Hidden
    to: Visible
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-templates
---

# Unhide a discussion template

## Trigger

A hidden template is needed again.

## Outcome

The template is offered again.
