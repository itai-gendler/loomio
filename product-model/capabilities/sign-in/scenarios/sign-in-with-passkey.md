---
kind: alternative
routes:
  web: Web
steps:
- text: The Visitor selects Use a passkey and unlocks it on their device
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product signs the Visitor in
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
---

# Sign in with a passkey

## Trigger

A person who added a passkey signs in with their device.

## Outcome

The person is signed in without entering an email address.
