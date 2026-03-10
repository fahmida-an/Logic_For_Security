# Week 7 - Class Presentation Outline

## Slide 1 - Title and Scenario
- Project: Open Authorization for photo-book printing.
- Roles:
  - `A`: photo owner
  - `B`: photo storage server
  - `P`/`p`: photo-book service
  - `I`: identity provider
- Goal: let `P` read selected photos from `B` without exposing full account access.

## Slide 2 - Week 2 Baseline (Dolev-Yao)
- File: `Week2_Problem2_First_AnB_Version.anb`
- Initial simple delegation model.
- Static Dolev-Yao analysis file:
  - `Week2_Problem3_Static_DolevYao_Analysis.md`
- Key finding: baseline secrecy can leak under attacker observation/model assumptions.

## Slide 3 - Week 3 IDP Integration + Lazy Intruder
- Main file: `Week3_Problem1_AnB_With_IdentityProvider.anb`
- Added identity provider and password proof:
  - `h(pw(A,I),NA)` (password not used as encryption key).
- Special task file:
  - `Week3_Problem2_LazyIntruder_Executability_of_P.md`
- Key finding: role executability shown; security issues still found in model checking.

## Slide 4 - Week 4 Formats + Key Lookup
- Main format file:
  - `Week4_Problem1_MainProtocol_Formats.anb`
- Separate key lookup:
  - `Week4_Problem2_AnB_KeyLookup_Protocol.anb`
- Type-flaw reasoning:
  - `Week4_Problem3_TypeFlawResistance_Check.md`
- Key finding: format-based structure improves protocol clarity and typing robustness.

## Slide 5 - Week 5 Pseudonymous Channels (TLS-style)
- File: `Week5_Problem1_PseudonymousChannels.anb`
- Goal: replace direct crypto expressions with channel abstraction (`*->*`, `[A]` style).
- Result summary:
  - `Week5_Problem1_PseudonymousChannels_Result.md`
- Key finding: channel abstraction works but still exposes weaknesses in this variant.

## Slide 6 - Week 6 Guessable Password Verification
- Baseline vulnerable check:
  - `Week6_Problem1_GuessablePassword_Check.anb` -> `guesswhat` attack found.
- Hardened version:
  - `Week6_Problem2_GuessablePassword_Hardened.anb`
- Focused special-task check:
  - `Week6_Problem3_GuessablePassword_OnlyCheck.anb`
  - OFMC (`--numSess 1`) -> `NO_ATTACK_FOUND` for guessable-password goal.

## Slide 7 - Main Lessons
- Iterative development is essential in protocol design.
- Passing syntax/executability does not mean security.
- Different goals fail differently (secrecy vs. weak authentication vs. guessing).
- Message formats and scoped assumptions significantly change verification outcomes.

## Slide 8 - Final Status and Next Steps
- Final narrative:
  - Week 2 -> baseline
  - Week 3 -> IDP + executability proof
  - Week 4 -> format and typing improvements
  - Week 5 -> channel abstraction
  - Week 6 -> guessable password analysis
- Future improvement:
  - remove remaining weak-auth/secrecy attacks while preserving delegation features.
