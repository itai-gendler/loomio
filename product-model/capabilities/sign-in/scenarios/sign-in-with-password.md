---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters their email address and password and selects Sign in
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product signs the Visitor in and offers to add a passkey if they have none
  kind: product
  actor: visitor
  entities:
  - entity: user
    effect: reads
    facts:
    - Email
  contexts:
    web:
      place: web::public::sign-in
---

# Sign in with email and password

## Trigger

A person with a password wants to use Loomio.

## Outcome

The person is signed in and returns to where they were going.
