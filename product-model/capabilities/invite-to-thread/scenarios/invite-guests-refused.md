---
kind: validation
routes:
  web: Web
steps:
- text: The User invites people from outside the group
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The plan does not allow guests, or the User is not an admin and members may not add guests
  kind: condition
  actor: user
  entities:
  - entity: subscription
    effect: reads
    facts:
    - Guests allowed
  - entity: group
    effect: reads
    facts:
    - Members can add guests
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product refuses the invitation
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Inviting guests is refused

## Trigger

Someone tries to invite people from outside the group without being allowed to.

## Outcome

Nobody is added to the thread.
