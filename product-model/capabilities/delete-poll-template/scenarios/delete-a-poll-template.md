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
      place: web::signed-in
- text: The Product deletes the template
  kind: product
  actor: user
  entities:
  - entity: poll-template
    effect: changes
    from: Visible
    to: Deleted
    facts: []
  contexts:
    web:
      place: web::signed-in
---

# Delete a poll template

## Trigger

A custom template is no longer needed.

## Outcome

The template is gone from the group.
