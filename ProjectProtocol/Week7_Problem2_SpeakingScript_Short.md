# Week 7 - Short Speaking Script (5-7 minutes)

## 1) Intro (30-45 sec)
"Our project models open authorization for photo printing. A wants to allow P to read selected photos at B, with trust anchored in identity provider I. We developed the protocol week by week and verified each version with OFMC."

## 2) Week 2 (45 sec)
"We started with a simple delegation protocol in AnB. Using Dolev-Yao analysis and OFMC, we observed that secrecy could fail in the baseline. This gave us a concrete starting point for refinement."

## 3) Week 3 (60 sec)
"We integrated the identity provider and password-based authentication proof using `h(pw(A,I),NA)` rather than using password as encryption key. We also completed the required lazy-intruder executability task for role P step by step."

## 4) Week 4 (60 sec)
"We introduced explicit message formats to reduce type confusion and made a separate key-lookup protocol where A queries I for public keys. We documented type-flaw-resistance reasoning based on message-pattern structure."

## 5) Week 5 (45 sec)
"We created a TLS-style channel abstraction variant using pseudonymous channels. This made the model closer to realistic channel assumptions, but attacks were still possible in our tested variant."

## 6) Week 6 (60-75 sec)
"We focused on guessable password security. The baseline guessable-password model was breakable. Then we hardened the password proof with extra freshness and checked a guessable-only model. For bounded sessions, this check returned no guessing attack."

## 7) Closing (30 sec)
"Main lesson: protocol security requires iterative modeling, explicit assumptions, and multiple goal checks. Secrecy, authentication, and guessing-resistance can fail independently, so each must be tested explicitly."

## Optional Q&A backup points
- Why include attack-found versions? -> They justify design decisions and show learning progression.
- Why separate key lookup? -> Week 4 requirement and realistic trust decomposition.
- Why bounded result in Week 6? -> OFMC bounded-session analysis; we report exactly what was verified.
