---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Revoke delegate for a delegate
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product stops the member being a delegate
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    facts:
    - Delegate
  contexts:
    web:
      place: web::signed-in::group
---

# Revoke a delegate

## Trigger

An admin removes someone's voting rights as a delegate.

## Outcome

The member is no longer a delegate.
