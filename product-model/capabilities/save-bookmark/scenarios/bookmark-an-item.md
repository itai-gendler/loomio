---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Save bookmark in the item's menu
  kind: actor
  actor: user
  entities:
  - entity: bookmark
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product saves the bookmark
  kind: product
  actor: user
  entities:
  - entity: bookmark
    effect: creates
    facts:
    - Item
    - Saved at
  contexts:
    web:
      place: web::signed-in::thread
---

# Bookmark an item

## Trigger

Someone wants to return to an item later.

## Outcome

The item is on the person's Bookmarks page; nobody else is told.
