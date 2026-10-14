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
      place: web::signed-in
- text: The Product shows the template again
  kind: product
  actor: user
  entities:
  - entity: poll-template
    effect: changes
    from: Hidden
    to: Visible
    facts: []
  contexts:
    web:
      place: web::signed-in
---

# Unhide a poll template

## Trigger

A hidden template is needed again.

## Outcome

The template is offered again.
