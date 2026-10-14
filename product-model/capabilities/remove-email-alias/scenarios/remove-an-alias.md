---
kind: primary
routes:
  web: Web
steps:
- text: The User removes an address from the group's email aliases
  kind: actor
  actor: user
  entities:
  - entity: email-alias
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product removes the alias
  kind: product
  actor: user
  entities:
  - entity: email-alias
    effect: removes
  contexts:
    web:
      place: web::signed-in::group
---

# Remove an email alias

## Trigger

An admin decides an address should be treated as unknown again.

## Outcome

The address is no longer recognized or blocked.
