---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Bookmarks
  kind: actor
  actor: user
  entities:
  - entity: bookmark
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::bookmarks
- text: The Product lists the User's bookmarks, newest first
  kind: product
  actor: user
  entities:
  - entity: bookmark
    effect: reads
    facts:
    - Item
    - Saved at
  contexts:
    web:
      place: web::signed-in::bookmarks
---

# Open your bookmarks

## Trigger

Someone returns to items they saved.

## Outcome

The person sees their bookmarks with each item's kind and author.
