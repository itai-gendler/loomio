---
kind: alternative
routes:
  web: Web
steps:
- text: The poll is anonymous and the User has not voted
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
- text: The User makes their choice, without a reason
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product stores the ballot without the User's name or the time, marks the User as having voted and confirms only that the vote was recorded
  kind: product
  actor: user
  entities:
  - entity: anonymous-ballot
    effect: creates
    facts:
    - Choices
    - None of the above
  - entity: anonymous-voter
    effect: changes
    from: Not voted
    to: Voted
    facts: []
  - entity: poll
    effect: changes
    facts:
    - Results
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Vote in an anonymous poll

## Trigger

A voter responds to an anonymous poll.

## Outcome

The ballot counts, the voter shows as having voted, and nothing links the two.

## Edge cases

- A submitted anonymous ballot cannot be reviewed, changed or withdrawn.
