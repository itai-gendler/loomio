---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the poll's votes
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::votes
- text: The Product lists the votes with choices, reasons and weights, filtered as the User asks
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts:
    - Choices
    - Reason
    - Weight
  contexts:
    web:
      place: web::signed-in::votes
---

# View a poll's votes

## Trigger

Someone wants to read how people voted and why.

## Outcome

The person sees the votes they may see, with reasons and weights.

## Edge cases

- Votes hidden by the poll's results setting are not listed until it allows.
