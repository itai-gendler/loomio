---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor tries to create an account without following an invitation
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The server lets people create accounts only through invitations
  kind: condition
  actor: visitor
  entities:
  - entity: server-settings
    effect: reads
    facts:
    - Sign-up
  contexts:
    web:
      place: web::public::sign-in
- text: The Product refuses and says an invitation is required
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
---

# Creating an account without an invitation is refused

## Trigger

Someone tries to create an account on a server that requires an invitation.

## Outcome

No account is created.
