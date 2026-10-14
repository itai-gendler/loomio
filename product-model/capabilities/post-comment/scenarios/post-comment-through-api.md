---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a comment for a discussion, or a reply to an item
  kind: actor
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts: []
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product adds the comment to the thread and notifies the people mentioned
  kind: product
  actor: user
  entities:
  - entity: comment
    effect: creates
    to: Visible
    facts:
    - Body
    - Reply to
    - Replies
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: api
---

# Post a comment through the API

## Trigger

An integration acting as a person comments on a discussion or replies to an item.

## Outcome

The comment shows in the thread.
