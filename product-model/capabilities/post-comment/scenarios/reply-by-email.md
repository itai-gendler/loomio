---
kind: alternative
routes:
  web: Web
steps:
- text: The User replies to a notification email
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: email
- text: The Product adds the reply's text and attachments to the thread as the User's comment on the item the email was about
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
      place: email
---

# Reply by email

## Trigger

A person replies to a notification email that says replies are accepted.

## Outcome

The reply appears in the thread as their comment, beneath the item the email was about.

## Edge cases

- Quoted earlier messages and signatures are left out of the comment.
