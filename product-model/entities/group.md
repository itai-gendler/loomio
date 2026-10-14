---
domain: group-settings
relations:
- entity: group
  verb: contains
  cardinality: one-to-many
- entity: membership
  verb: has
  cardinality: one-to-many
- entity: membership-request
  verb: receives
  cardinality: one-to-many
- entity: thread
  verb: holds
  cardinality: one-to-many
- entity: tag
  verb: owns
  cardinality: one-to-many
- entity: poll-template
  verb: keeps
  cardinality: one-to-many
- entity: discussion-template
  verb: keeps
  cardinality: one-to-many
- entity: group-follow
  verb: is-followed-through
  cardinality: one-to-many
- entity: unrecognized-email
  verb: holds-for-review
  cardinality: one-to-many
- entity: email-alias
  verb: recognizes
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: app/models/group.rb
- kind: code
  role: implementation
  target: app/models/concerns/group_privacy.rb
- kind: code
  role: implementation
  target: app/models/permitted_params.rb#group_attributes
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/privacy.md
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/permissions.md
---

# Group

A group of people who discuss and decide together. A top-level group is an organization; it may contain subgroups, each with its own members, privacy and permissions. Group settings decide who can find the group, how people join and which actions ordinary members may take beside the admins.

## Information kept

- **Name** — the group's name
- **Handle** — the short name in the group's address; an old handle keeps redirecting after it changes
- **Description** — what the group is for
- **Parent group** — the organization a subgroup belongs to; absent for a top-level group
- **Privacy** — Open, Closed, Visible to parent group or Secret
- **Discussion privacy** — Public only, Private only, or Public or private: whether threads in the group are public, private or chosen per thread
- **How people join** — Join without approval, Request to join, or Invitation only
- **Joining prompt** — the question people answer when they request to join
- **Listed in directory** — whether an Open or Closed top-level group appears in the public group directory
- **Members can add members** — whether ordinary members may invite people and review membership requests
- **Members can add guests** — whether ordinary members may invite people from outside the group into a thread
- **Members can announce** — whether ordinary members may notify the whole group
- **Members can start discussions** — whether ordinary members may start discussions
- **Non-members can start discussions** — whether people who can see a non-secret group but are not members may start discussions in it
- **Members can edit discussions** — whether ordinary members may edit any discussion's context and write poll outcomes
- **Members can edit comments** — whether members may edit their own comments
- **Members can delete comments** — whether members may permanently delete their own comments
- **Members can start polls** — whether ordinary members may start proposals and polls
- **Members can create subgroups** — whether ordinary members may start subgroups
- **Members can create tags** — whether ordinary members may create new tags
- **Members can create templates** — whether ordinary members may create discussion and poll templates
- **Admins can edit member comments** — whether admins may edit comments other people wrote
- **Parent members can see discussions** — whether members of the parent group may read a parent-visible subgroup's threads
- **Admin count** — how many admins the group currently has
- **Hidden templates** — the built-in poll templates the group has hidden from people starting a vote
- **Shared link** — the link that lets anyone holding it join the group; resetting it replaces it

## States

### Active

The group is in use.

### Deleted

An admin or Instance administrator deleted the group, together with its subgroups. Nobody can open it; it is permanently removed after the grace period.
