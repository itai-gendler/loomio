---
references:
- kind: code
  role: implementation
  target: app/models/topic_reader.rb
- kind: code
  role: implementation
  target: app/models/ability/topic_reader.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/topic_readers_controller.rb
---

# Thread member

A person's standing in one thread beyond their group membership: guest access for someone outside the group, the thread admin role, and how they are notified. Whoever starts a discussion becomes its thread admin.

## Information kept

- **Guest** — whether the person reaches the thread as a guest rather than through the group
- **Thread admin** — whether the person administers this thread
- **Email notifications** — All activity, When notified, or None, for this thread
- **Invited by** — who invited the person into the thread

## States

### Active

The person has their standing in the thread.

### Removed

A thread admin removed the guest from the thread.
