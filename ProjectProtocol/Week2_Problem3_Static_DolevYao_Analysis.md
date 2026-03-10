# Week 2 - Problem 3: Static Dolev-Yao Analysis (Passive Intruder)

This analysis follows the required setting:
- honest agents run the protocol;
- intruder only observes traffic and does not inject messages.

Protocol analyzed: `Week2_Problem2_First_AnB_Version.anb`

## Mapping to Project Scenario
- `A`: resource owner (photo account owner)
- `B`: photo storage server
- `P`: photo-book service that requests delegated read access
- `F`: selected folder/collection to be printed
- `T`: validity/expiry value
- `Photos`: photo data returned by `B`

## Observed Messages
1. `A -> P: {A,B,P,F,T}inv(pk(A))`
2. `P -> B: {A,B,P,F,T}inv(pk(A)),F`
3. `B -> P: {Photos}pk(P)`

## Passive Intruder Knowledge Growth (Dolev-Yao)
Let initial public knowledge contain agent names and public keys.

- From (1): by `OpenSig`, intruder derives `A,B,P,F,T`.
- From (2): no new secret beyond `F` (already derivable).
- From (3): ciphertext is `{Photos}pk(P)`.
- Since intruder knows `inv(pk(P))` when playing role `P`, he can derive `Photos` by `DecAsym`.

## Conclusion
In this first Week-2 draft, a passive Dolev-Yao intruder can derive `Photos`.
So secrecy goal for delegated photo access is not met in this baseline version.

## Why this is still useful
This is a valid development snapshot for the logbook:
- protocol is executable and captures core idea;
- attack surface is visible early;
- Week 3/4 refinements can now target exactly this leak.
