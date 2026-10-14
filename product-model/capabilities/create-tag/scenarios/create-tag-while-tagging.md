---
kind: alternative
routes:
  web: Web
steps:
- text: The User types a new tag name and presses Enter
  kind: actor
  actor: user
  entities:
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The User is an admin, or the group lets members create tags
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Members can create tags
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product creates the tag and applies it to the thread
  kind: product
  actor: user
  entities:
  - entity: tag
    effect: creates
    facts:
    - Name
    - Color
  - entity: thread
    effect: changes
    facts:
    - Tags
  contexts:
    web:
      place: web::signed-in::thread
---

# Create a tag while tagging

## Trigger

A member types a tag name that does not exist yet while tagging a thread.

## Outcome

The new tag exists for the organization and is on the thread.

## Edge cases

- Without permission to create tags, members can still apply existing ones.
