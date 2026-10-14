---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects Reply on a comment and writes a reply that mentions its author
  kind: actor
  actor: user
  entities:
  - entity: comment
    as: original
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product adds the reply beneath the comment and notifies the people mentioned
  kind: product
  actor: user
  entities:
  - entity: comment
    as: reply
    effect: creates
    to: Visible
    facts:
    - Body
    - Reply to
    - Replies
  - entity: comment
    as: original
    effect: changes
    facts:
    - Replies
  contexts:
    web:
      place: web::signed-in::thread
---

# Reply to a comment

## Trigger

Someone answers a particular comment.

## Outcome

The reply sits beneath the comment it answers and its author is notified through the mention.
