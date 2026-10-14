---
kind: primary
routes:
  web: Web
steps:
- text: The person's catch-up is due and they have unseen notifications or unread activity
  kind: condition
  unattended: true
  entities:
  - entity: user
    effect: reads
    facts:
    - Catch-up email
    - Time zone
  contexts:
    web:
      place: web::signed-in::notification-settings
- text: The Product emails the catch-up, notifications first, then unread activity by group, including followed Open groups
  kind: product
  entities:
  - entity: user
    effect: reads
    facts:
    - Email
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::notification-settings
---

# The catch-up email is sent

## Trigger

The morning of a person's catch-up day arrives in their time zone.

## Outcome

The person has one email with their unseen notifications and unread activity, or none when there is nothing new.

## Edge cases

- The Unsubscribe link in a catch-up email opens a catch-up form that works without signing in.
