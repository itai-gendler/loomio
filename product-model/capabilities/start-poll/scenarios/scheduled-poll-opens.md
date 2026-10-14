---
kind: primary
routes:
  web: Web
steps:
- text: The opening time of a scheduled poll has arrived
  kind: condition
  unattended: true
  entities:
  - entity: poll
    effect: reads
    facts:
    - Opening time
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product opens the poll for voting and notifies the voters when it is set to
  kind: product
  entities:
  - entity: poll
    effect: changes
    from: Scheduled
    to: Open
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# A scheduled poll opens

## Trigger

The opening time of a scheduled poll arrives.

## Outcome

Voting is open and, unless the coordinator turned it off, voters are notified.
