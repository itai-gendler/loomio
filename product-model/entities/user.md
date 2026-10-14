---
kind: person
acts: external
relations:
- entity: membership
  verb: holds
  cardinality: one-to-many
- entity: membership
  verb: invites
  cardinality: one-to-many
- entity: membership-request
  verb: sends
  cardinality: one-to-many
- entity: thread-member
  verb: holds
  cardinality: one-to-many
- entity: discussion
  verb: starts
  cardinality: one-to-many
- entity: comment
  verb: writes
  cardinality: one-to-many
- entity: vote
  verb: casts
  cardinality: one-to-many
- entity: anonymous-voter
  verb: is-listed-as
  cardinality: one-to-many
- entity: outcome
  verb: writes
  cardinality: one-to-many
- entity: bookmark
  verb: saves
  cardinality: one-to-many
- entity: reaction
  verb: adds
  cardinality: one-to-many
- entity: group-follow
  verb: follows-with
  cardinality: one-to-many
- entity: poll-template
  verb: authors
  cardinality: one-to-many
- entity: discussion-template
  verb: authors
  cardinality: one-to-many
- entity: task
  verb: is-assigned
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: app/models/user.rb
- kind: code
  role: implementation
  target: app/models/ability/user.rb
- kind: code
  role: implementation
  target: app/services/user_service.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/users/user_profile/index.md
- kind: doc
  role: intent
  target: docs/en/user_manual/users/email_settings/index.md
---

# User

A person with their own Loomio account. What a User may do in a group or thread comes from the Membership or Thread member they hold there; the same person is a member in one group, an admin in another and a guest in a single thread elsewhere. A deactivated account leaves every group but keeps its name on what it wrote; a deleted account also loses its name, email address and profile.

## Information kept

- **Name** — the name shown beside everything the person writes
- **Email** — the address invitations, notifications and sign-in links go to
- **Email verified** — whether the person has confirmed their email address; starting groups, discussions and subgroups needs it
- **Deactivated** — whether the person has deactivated their account; a deactivated person no longer votes
- **Username** — the name people type to @mention the person
- **Introduction** — a few lines the person writes about themselves
- **Location** — where the person is, shown on their profile
- **Language** — the language Loomio is shown in, detected from the browser until the person chooses one
- **Time zone** — the time zone dates are shown in and catch-up emails are timed by
- **Translate automatically** — whether other people's content is translated into the person's language without asking
- **Email notifications default** — Catch-up only, When notified or All activity, given to each group the person joins
- **Catch-up email** — Never, Every day, Every second day, or a weekday for a weekly catch-up
