---
kind: alternative
routes:
  web: Web
steps:
- text: The Visitor selects Send me a code and enters their email address
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product emails a six-digit code when the address belongs to an account, showing the same confirmation either way
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Visitor enters the code
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product signs the Visitor in and offers to set a password or add a passkey
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
---

# Sign in with an emailed code

## Trigger

A person without a password, or who forgot it, asks for a code.

## Outcome

The person is signed in and is offered to set a password or add a passkey.

## Edge cases

- A code expires after a day and works once.
