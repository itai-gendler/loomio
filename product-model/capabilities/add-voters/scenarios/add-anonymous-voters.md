---
kind: alternative
routes:
  web: Web
steps:
- text: The poll is anonymous and still open
  kind: condition
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Anonymous
  contexts:
    web:
      place: web::signed-in::thread
- text: The User picks people to add
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product lists each person as an anonymous voter and notifies them when asked
  kind: product
  actor: user
  entities:
  - entity: anonymous-voter
    effect: creates
    to: Not voted
    facts:
    - Group member
    - Invited by
  contexts:
    web:
      place: web::signed-in::thread
---

# Add voters to an anonymous poll

## Trigger

A poll admin adds people to an open anonymous poll.

## Outcome

Each person added is listed as an anonymous voter who has not voted.
