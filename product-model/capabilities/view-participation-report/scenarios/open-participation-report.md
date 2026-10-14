---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses groups, dates and interval, optionally delegates only
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::participation-report
- text: The Product counts threads, comments, polls, votes and reactions for the chosen groups the User belongs to, and each person's voting record outside anonymous polls
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: reads
    facts:
    - Delegate
  - entity: vote
    effect: reads
    facts:
    - Cast at
  - entity: reaction
    effect: reads
    facts: []
  - entity: comment
    effect: reads
    facts: []
  - entity: thread
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::participation-report
---

# Open a participation report

## Trigger

A member wants to understand participation in their group.

## Outcome

The member sees the report for the groups they belong to.
