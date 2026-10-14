---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor selects Create account and enters their email address
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product emails a code to prove the address, or skips it when the person followed an invitation to that address
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Visitor enters the code, their name and accepts the terms
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product creates the account with notification defaults and signs the Visitor in
  kind: product
  actor: visitor
  entities:
  - entity: user
    effect: creates
    facts:
    - Name
    - Email
    - Email verified
    - Language
    - Time zone
    - Email notifications default
    - Catch-up email
  contexts:
    web:
      place: web::public::sign-in
---

# Create an account

## Trigger

A person new to Loomio wants an account.

## Outcome

The account exists with a verified email address and the person is signed in.

## Edge cases

- Use the address that received the invitation, so the invitation is accepted with the new account.
