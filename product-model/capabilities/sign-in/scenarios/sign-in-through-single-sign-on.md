---
kind: alternative
routes:
  web: Web
steps:
- text: The server offers no sign-in of its own
  kind: condition
  actor: visitor
  entities:
  - entity: server-settings
    effect: reads
    facts:
    - Local sign-in
  contexts:
    web:
      place: web::public::sign-in
- text: The Visitor selects the organization's sign-in and signs in there
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

# Sign in through the organization's single sign-on

## Trigger

A person opens a server that offers only its organization's single sign-on.

## Outcome

The person is signed in through the organization.
