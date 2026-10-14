---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the poll's details, options or closing time
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product saves the poll and notifies anyone the User chose
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: changes
    facts:
    - Details
    - Options
    - Closing time
  contexts:
    web:
      place: web::signed-in::poll-form
---

# Edit a poll

## Trigger

A poll admin needs to correct or extend a poll.

## Outcome

The poll shows the changes and, when asked, the chosen people are notified.

## Edge cases

- Turning vote weights on or off resets every vote's weight to the voter's member weight, or to one.
