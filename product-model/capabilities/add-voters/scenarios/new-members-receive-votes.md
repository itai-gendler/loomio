---
kind: primary
routes:
  web: Web
steps:
- text: A person joined while a poll open to everyone had not closed
  kind: condition
  unattended: true
  entities:
  - entity: poll
    effect: reads
    facts:
    - Who can vote
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product gives the newcomer a vote, or lists them among an anonymous poll's voters
  kind: product
  entities:
  - entity: vote
    effect: creates
    to: Undecided
    facts:
    - Weight
    - Invited by
  - entity: anonymous-voter
    effect: creates
    to: Not voted
    facts:
    - Group member
    - Invited by
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# New members receive a vote

## Trigger

Someone joins the group, or becomes a guest of the thread, while a poll open to everyone has not closed.

## Outcome

The newcomer can vote in that poll without being invited separately.
