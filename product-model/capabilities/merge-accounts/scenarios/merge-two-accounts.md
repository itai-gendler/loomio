---
kind: primary
routes:
  web: Web
steps:
- text: The User, signed in to the account to retire, selects Merge accounts and enters the address of the account to keep
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::profile
- text: The Product emails a verification link to that address when an account uses it, shows the same confirmation either way and signs the User out
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::profile
- text: The User follows the link, signs in to the account to keep and confirms the merge after checking both addresses
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::merge-accounts
- text: The Product moves the retired account's memberships, discussions, comments, polls and votes to the kept account, deletes the retired account and emails a confirmation
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    facts:
    - Person
  - entity: user
    as: retired
    effect: removes
  - entity: discussion
    effect: reads
    facts: []
  - entity: comment
    effect: reads
    facts: []
  - entity: poll
    effect: reads
    facts: []
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::merge-accounts
---

# Merge two accounts

## Trigger

A person has accounts under two addresses and wants to keep one.

## Outcome

One account holds the memberships and activity of both; the other is deleted and its address no longer signs in.

## Edge cases

- Where both accounts belong to the same group, the kept account's Membership remains.
- A merge cannot be undone.
