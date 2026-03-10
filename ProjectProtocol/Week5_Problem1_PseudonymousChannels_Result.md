# Week 5 - Problem 1 Result (Pseudonymous Channels)

Protocol file:
- `Week5_Problem1_PseudonymousChannels.anb`

Command used:
- `ofmc --numSess 2 "ProjectProtocol\Week5_Problem1_PseudonymousChannels.anb"`

Result:
- `SUMMARY: ATTACK_FOUND`
- `GOAL: secrets`
- leaked term: `fData(Photos(1))`

Interpretation:
- The Week 5 model correctly uses OFMC pseudonymous channels (`*->*` and `[A]`).
- OFMC still finds an attack on secrecy in this variant.
- This is acceptable as a development snapshot and can be discussed in the report as a limitation/attack trace for the channel-based version.
