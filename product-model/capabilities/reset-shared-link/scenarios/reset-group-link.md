---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Reset this link
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product makes a new shared link for the group
  kind: product
  actor: user
  entities:
  - entity: group
    effect: changes
    facts:
    - Shared link
  contexts:
    web:
      place: web::signed-in::group
---

# Reset the shared link

## Trigger

The group's link was shared too widely.

## Outcome

The old link no longer works and a new one is shown.
