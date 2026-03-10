# Week 2 - Problem 1: Informal Protocol Outline

## Goal (Mapped to Project Text)
This models the project scenario directly:
- `A`: account owner (the person with holiday photos)
- `B`: photo storage server/resource server
- `P`: photo-book printing service

`A` wants to let `P` read only selected photos on `B` without sharing full account credentials.

## Simplified Assumptions for Week 2
- We simplify key management: all public keys are already known.
- No identity provider yet (added in Week 3).
- We model one authorization scope as a token.
- The token is intended to represent read-only access to one selected photo folder/set.

## Informal Message Flow (First Draft)
1. `P -> A`: "Please allow me to read your selected photos on server `B`" (request + nonce).
2. `A -> P`: signed authorization statement bound to (`P`, `B`, scope, nonce, token).
3. `P -> B`: forwards `A`'s authorization and requests the approved photo scope.
4. `B -> P`: returns encrypted photo data under the session token.

## Initial Security Intent
- `B` only accepts access requests that are authorized by `A`.
- Authorization is bound to both `P` (delegate) and `B` (resource server).
- Photo data should only become available to the authorized `P`.
- The authorization should be scoped (selected folder/photos, not all resources).

## Known Limitation of this Week-2 Draft
- The model is intentionally minimal and may leak data under Dolev-Yao analysis.
- We use this version as baseline for iterative improvement in later weeks.
