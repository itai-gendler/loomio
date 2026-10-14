---
kind: primary
routes:
  web: Web
steps:
- text: The User selects the remove-bookmark button on the Bookmarks page
  kind: actor
  actor: user
  entities:
  - entity: bookmark
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::bookmarks
- text: The Product removes the bookmark
  kind: product
  actor: user
  entities:
  - entity: bookmark
    effect: removes
  contexts:
    web:
      place: web::signed-in::bookmarks
---

# Remove a bookmark

## Trigger

A saved item is no longer needed.

## Outcome

The item is no longer on the person's Bookmarks.
