---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Set title for a member and enters a title
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

# An admin sets a member's title

## Trigger

An admin labels a member, before or after they accept their invitation.

## Outcome

The member's title shows beside their name in this group.
