---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Sign out
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in
- text: The Product signs the User out
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in
---

# Sign out

## Trigger

A person finishes using Loomio, for example on a shared computer.

## Outcome

The person is signed out.
