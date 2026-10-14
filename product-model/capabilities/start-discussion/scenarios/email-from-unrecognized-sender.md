---
kind: edge
routes:
  web: Web
steps:
- text: The User emails the group's address from an address the group does not know
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: email
- text: The sender's address matches no member and no recognized alias
  kind: condition
  actor: user
  entities:
  - entity: email-alias
    effect: reads
    facts:
    - Address
  contexts:
    web:
      place: email
- text: The Product holds the email for the group's admins and notifies them
  kind: product
  actor: user
  entities:
  - entity: unrecognized-email
    effect: creates
    to: Waiting
    facts:
    - Sender
    - Subject
    - Body
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: email
---

# Email to a group from an unrecognized sender

## Trigger

Someone emails the group's address from an address that matches no member.

## Outcome

No discussion starts; the email waits and the group's admins are notified to recognize or block the sender.

## Edge cases

- Email from an address the group blocked is dropped.
