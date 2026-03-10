# Week 6 - Guessable Password Check (Summary)

## Files
- `Week6_Problem1_GuessablePassword_Check.anb`
- `Week6_Problem2_GuessablePassword_Hardened.anb`
- `Week6_Problem3_GuessablePassword_OnlyCheck.anb`

## OFMC Results

### 1) Baseline guessable check
Command:
- `ofmc --numSess 2 "ProjectProtocol\Week6_Problem1_GuessablePassword_Check.anb"`

Result:
- `ATTACK_FOUND`
- `GOAL: guesswhat`

Interpretation:
- Password usage in this baseline is vulnerable to offline guessing in OFMC's guessable-secret model.

### 2) Hardened variant (adds fresh `K` into password proof)
Command:
- `ofmc --numSess 2 "ProjectProtocol\Week6_Problem2_GuessablePassword_Hardened.anb"`

Result:
- `ATTACK_FOUND`
- `GOAL: secrets` (not `guesswhat`)

Interpretation:
- Guessing attack is no longer the first issue found.
- A separate secrecy weakness still exists in this protocol variant.

### 3) Guessable-only verification
Command:
- `ofmc --numSess 1 "ProjectProtocol\Week6_Problem3_GuessablePassword_OnlyCheck.anb"`

Result:
- `NO_ATTACK_FOUND`
- `DETAILS: BOUNDED_NUMBER_OF_SESSIONS`

Interpretation:
- For this bounded check, the password is not broken via the guessable-secret goal.
- This directly addresses the Week 6 special-task focus (guessable password robustness), within the tested session bound.
