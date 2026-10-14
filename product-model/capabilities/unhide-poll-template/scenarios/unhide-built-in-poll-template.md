---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects Unhide on a hidden built-in template
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in
- text: The Product removes the template from the group's hidden templates
  kind: product
  actor: user
  entities:
  - entity: group
    effect: changes
    facts:
    - Hidden templates
  contexts:
    web:
      place: web::signed-in
---

# Unhide a built-in poll template

## Trigger

An admin wants a hidden built-in template back.

## Outcome

The built-in template is offered again.
