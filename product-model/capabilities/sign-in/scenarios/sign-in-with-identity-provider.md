---
kind: alternative
routes:
  web: Web
steps:
- text: The Visitor chooses an identity provider among the sign-in options
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Visitor signs in at the identity provider
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product signs the Visitor in, linking the provider to the account with the same email address
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

# Sign in with an identity provider

## Trigger

A person chooses Google, or another provider the server offers beside its own sign-in.

## Outcome

The person is signed in; an account with the same email address is linked to the provider.
