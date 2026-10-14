---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor enters an email address and password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The details do not match an active account
  kind: condition
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product refuses with the same message whatever was wrong
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
---

# Sign-in with wrong details is refused

## Trigger

Someone enters details that do not open an active account.

## Outcome

Nobody is signed in and the message does not say which detail was wrong.

## Edge cases

- An account still missing its name or terms acceptance is completed before the person is signed in.
