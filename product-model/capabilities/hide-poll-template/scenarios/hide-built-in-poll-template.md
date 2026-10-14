---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects Hide on a built-in template
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in
- text: The Product adds the template to the group's hidden templates
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

# Hide a built-in poll template

## Trigger

An admin wants Loomio's built-in templates the group does not use out of the list.

## Outcome

The built-in template is no longer offered in the group.

## Edge cases

- Built-in templates can be hidden or adapted, never deleted.
