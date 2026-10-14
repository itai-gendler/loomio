---
kind: validation
routes:
  web: Web
steps:
- text: The User saves privacy settings
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group-settings
- text: An Open group would allow private discussions, a hidden group would allow public ones, or a public subgroup would sit under a hidden parent
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Privacy
    - Discussion privacy
    - Parent group
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group-settings
- text: The Product refuses to save the settings
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group-settings
---

# A contradictory privacy is refused

## Trigger

An admin chooses settings that contradict each other or the parent group.

## Outcome

Nothing is saved and the form names the conflicting setting.
