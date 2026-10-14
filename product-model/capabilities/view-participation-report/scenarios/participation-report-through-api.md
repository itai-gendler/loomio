---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration asks for a report with groups and dates
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product returns the report for the groups the User belongs to
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: reads
    facts:
    - Delegate
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: api
---

# Get a participation report through the API

## Trigger

An integration acting as a person asks for the report.

## Outcome

The integration has the same report.
