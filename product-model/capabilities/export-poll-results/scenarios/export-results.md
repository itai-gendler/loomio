---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Export on a poll whose results are available
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product produces the results with the votes the User may see
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Results
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Export a poll's results

## Trigger

Someone wants to analyze a poll's results elsewhere.

## Outcome

The person has the results file.

## Edge cases

- An anonymous STV Election exports its ballots without voters.
