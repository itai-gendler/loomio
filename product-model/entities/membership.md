---
domain: members
references:
- kind: code
  role: implementation
  target: app/models/membership.rb
- kind: code
  role: implementation
  target: app/services/membership_service.rb
- kind: code
  role: implementation
  target: app/models/ability/membership.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/member_management/index.md
---

# Membership

A person's place in one group. An invitation is already a Membership: the invited person counts among the group's members, receives votes in its polls and notifications, before they accept. Only an Invited or Active Membership makes its person a member; a Removed one grants nothing.

## Information kept

- **Person** — the account holding the Membership
- **Role** — Member or Admin
- **Delegate** — whether the member is one of the group's delegates, the people chosen to vote when a poll is limited to them
- **Title** — a label for the member's role or the organization they represent in this group
- **Vote weight** — the weight the member's votes carry in polls that use vote weights
- **Invited by** — who invited or added the person
- **Accepted at** — when the person accepted the invitation or joined
- **Email notifications** — Catch-up only, When notified or All activity for this group; each thread starts from it

## States

### Invited

The person has been invited and has not yet followed the invitation.

### Active

The person joined, accepted an invitation or was approved.

### Removed

The person left, was removed, or the invitation was cancelled. Inviting or adding them again brings the same Membership back.
