---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Hide on the template
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in
- text: The Product hides the template
  kind: product
  actor: user
  entities:
  - entity: poll-template
    effect: changes
    from: Visible
    to: Hidden
    facts: []
  contexts:
    web:
      place: web::signed-in
---

# Hide a poll template

## Trigger

A template is not needed for now.

## Outcome

The template is no longer offered but is kept under hidden templates.
