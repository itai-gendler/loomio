---
entities:
- entity: vote
  shows:
  - Choices
  - Reason
  - Weight
- entity: anonymous-voter
  shows:
  - Group member
- entity: poll
  shows:
  - Title
entryPoints:
- web: /p/{key}/votes
---

# Votes

One poll's votes, or an anonymous poll's participation.
