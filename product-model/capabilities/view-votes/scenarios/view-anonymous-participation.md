---
kind: alternative
routes:
  web: Web
steps:
- text: The poll is anonymous and its results are available
  kind: condition
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Anonymous
    - Closed at
  contexts:
    web:
      place: web::signed-in::votes
- text: The User opens the poll's voters
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::votes
- text: The Product lists the eligible people and whether each took part
  kind: product
  actor: user
  entities:
  - entity: anonymous-voter
    effect: reads
    facts:
    - Group member
  contexts:
    web:
      place: web::signed-in::votes
---

# See who took part in an anonymous poll

## Trigger

Results of an anonymous poll are available.

## Outcome

The person sees who was eligible and who took part, never what anyone chose.
