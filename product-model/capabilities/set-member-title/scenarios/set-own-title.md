---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Set title for themselves and enters a title
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product saves the title
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    facts:
    - Title
  contexts:
    web:
      place: web::signed-in::group
---

# Set your own title

## Trigger

A member wants others to know their role in the group.

## Outcome

The member's title shows beside their name in this group.
