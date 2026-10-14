---
domain: polls
relations:
- entity: vote
  verb: has
  cardinality: one-to-many
- entity: anonymous-voter
  verb: has
  cardinality: one-to-many
- entity: anonymous-ballot
  verb: receives
  cardinality: one-to-many
- entity: outcome
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: app/models/poll.rb
- kind: code
  role: implementation
  target: app/services/poll_service.rb
- kind: code
  role: implementation
  target: config/poll_types.yml
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/settings/index.md
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/intro_to_decisions/index.md
---

# Poll

A proposal or poll that collects structured responses. Its poll type decides how people respond and how results are counted: a proposal, sense check, opt-in count or question asks for a position, Choose picks options, Score rates every option, Allocate distributes a budget of dots, Rank orders options, Time poll finds when people are available, and STV Election elects several winners. Anonymity and the voting method are fixed once the poll exists.

## Information kept

- **Title** — the poll's title
- **Details** — what people are asked to respond to
- **Poll type** — Proposal, Sense check, Count, Question, Choose, Score, Allocate, Rank, Time poll or STV Election
- **Options** — the options people choose among, with each option's name, icon, meaning and reason prompt; dates for a time poll
- **Closing time** — when voting closes; a poll without one is a draft
- **Opening time** — when a scheduled poll opens for voting
- **Closed at** — when voting closed
- **Anonymous** — whether votes are stored apart from who cast them
- **Who can vote** — Everyone in the thread, or Selected people only
- **Hide results** — Off, Until vote, or Until closed
- **Vote reason** — Disabled, Optional, Required, Required for disagree or block, or Required for block
- **Reason length limit** — whether vote reasons are limited to 500 characters
- **Closing soon reminder** — Nobody, Author, Undecided voters or All voters, reminded a day before closing
- **Notify on open** — whether voters are notified when voting opens
- **Quorum** — the share of eligible voters that must vote, when one is set
- **Vote weights** — whether each vote counts with its voter's weight
- **None of the above** — whether voters may choose none of the options
- **Ballot limits** — the limits the poll's voting method sets on a ballot: the fewest and most options chosen, the score range, the dots each voter allocates, or the seats an STV Election fills and how it counts
- **Results** — the counts, percentages and voters for each option, and how many eligible voters have not voted

## States

### Open

Voting is open until the closing time.

### Draft

The poll has no closing time yet; nobody can vote.

### Scheduled

The poll opens for voting at its opening time; people can see it but not vote.

### Closed

Voting has closed and results are final unless it is reopened.

### Deleted

The poll was deleted; its place in the thread shows it was removed.
