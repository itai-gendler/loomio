---
kind: primary
routes:
  web: Web
steps:
- text: The User picks the member the email came from
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product records the address as the member's alias and starts the discussion from the email
  kind: product
  actor: user
  entities:
  - entity: email-alias
    effect: creates
    facts:
    - Address
    - Member
    - Added by
  - entity: unrecognized-email
    effect: changes
    from: Waiting
    to: Accepted
    facts: []
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# Recognize a sender as a member

## Trigger

An admin sees an email from a member's other address.

## Outcome

The address is a recognized alias of the member and the email becomes a discussion.

## Edge cases

- Trial and demo groups cannot add aliases.
