---
kind: primary
routes:
  web: Web
steps:
- text: The User writes a comment and selects Post Comment
  kind: actor
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product adds the comment to the thread, marks it read for the User and notifies the people mentioned
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
      place: web::signed-in::thread
---

# Post a comment

## Trigger

A member or guest wants to contribute to the discussion.

## Outcome

The comment shows in the thread and the people mentioned are notified.

## Edge cases

- Mentioning someone gives them no access to the thread.
