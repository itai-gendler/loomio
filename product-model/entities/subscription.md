---
relations:
- entity: group
  verb: covers
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: app/models/subscription.rb
- kind: code
  role: implementation
  target: app/models/group.rb#subscription_active?
---

# Subscription

The plan a top-level group and all of its subgroups run under. A group without a paid plan runs under the free plan, which never lapses.

## Information kept

- **Plan** — the plan's name, such as free, trial or a paid plan
- **Status** — Active, or Lapsed once the plan has expired or been cancelled; a group under a lapsed plan is disabled
- **Guests allowed** — whether people outside the group may be invited into its threads
- **Member limit** — the most people the organization may have across the group and its subgroups, when the plan sets one
- **Thread limit** — the most threads the organization may hold, when the plan sets one
