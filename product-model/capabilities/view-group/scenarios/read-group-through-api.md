---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration asks for a group, or for its discussions or polls
  kind: actor
  actor: user
  entities:
  - entity: discussion
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
      place: api
- text: The Product returns the group with the discussions and polls the User may read, filtered by status when asked
  kind: product
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
    - Description
  - entity: discussion
    effect: reads
    facts:
    - Title
  - entity: poll
    effect: reads
    facts:
    - Title
    - Closing time
  contexts:
    web:
      place: api
---

# Read a group and its threads through the API

## Trigger

An integration acting as a person asks for a group and the discussions and polls in it.

## Outcome

The integration has the group and the discussions and polls the person may read.

## Edge cases

- Listing groups returns every group the person belongs to, including groups whose plan has lapsed.
