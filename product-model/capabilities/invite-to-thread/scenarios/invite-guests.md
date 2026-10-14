---
kind: primary
routes:
  web: Web
steps:
- text: The User enters email addresses or names and an optional message
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The group's plan allows guests
  kind: condition
  actor: user
  entities:
  - entity: subscription
    effect: reads
    facts:
    - Guests allowed
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product adds each new person to the thread as a guest, gives them a vote in its polls open to everyone that have not closed, and notifies everyone chosen
  kind: product
  actor: user
  entities:
  - entity: thread-member
    effect: creates
    to: Active
    facts:
    - Guest
    - Thread admin
    - Email notifications
    - Invited by
  - entity: vote
    effect: creates
    to: Undecided
    facts:
    - Weight
    - Invited by
  - entity: thread
    effect: reads
    facts: []
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Invite guests to a thread

## Trigger

Someone wants a person outside the group to take part in one thread.

## Outcome

Each guest can read and take part in this thread only, holds a vote in its polls open to everyone, and has been notified.

## Edge cases

- A guest sees no other discussions in the group unless invited to them too.
