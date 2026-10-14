---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Redact on a vote and confirms
  kind: actor
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product hides the reason and attachments and keeps the vote in the results
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: changes
    facts:
    - Reason redacted
  contexts:
    web:
      place: web::signed-in::thread
---

# Redact a vote reason

## Trigger

A poll admin finds a reason that should not stay visible.

## Outcome

The reason shows as redacted; the vote still counts.
