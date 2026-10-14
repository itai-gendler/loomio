---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Permanently delete account and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::profile
- text: The Product removes the account's name, email address and profile, deactivates it and removes it from every group, keeping its cast votes
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Name
    - Email
    - Username
    - Introduction
    - Location
    - Deactivated
  - entity: membership
    effect: changes
    from: Active
    to: Removed
    facts: []
  - entity: vote
    effect: changes
    from: Undecided
    to: Removed
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::profile
---

# Delete your account

## Trigger

A person wants their account and personal details gone.

## Outcome

Nobody can sign in to the account; comments, discussions and cast votes remain without the person's name.

## Edge cases

- Deleting an account does not cancel a paid plan.
