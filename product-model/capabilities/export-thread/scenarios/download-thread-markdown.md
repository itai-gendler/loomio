---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Markdown and copies or downloads it
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: 'The Product produces the thread as Markdown with what the User may see: context, comments, polls, results, votes and outcomes'
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts:
    - Tags
  - entity: discussion
    effect: reads
    facts:
    - Title
    - Context
  - entity: comment
    effect: reads
    facts:
    - Body
  - entity: poll
    effect: reads
    facts:
    - Results
  - entity: outcome
    effect: reads
    facts:
    - Statement
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Save a thread as Markdown

## Trigger

Someone wants meeting minutes or an archive of a decision.

## Outcome

The person has the whole thread as Markdown, in thread order, with front matter linking back to it.

## Edge cases

- While a poll hides results until voting, Print and Markdown wait until the User has voted.
- Voters in anonymous polls are never named.
