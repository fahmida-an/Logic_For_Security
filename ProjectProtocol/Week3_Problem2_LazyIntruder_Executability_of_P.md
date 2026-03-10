# Week 3 - Problem 2: Lazy Intruder Executability of Role `P`

Protocol analyzed: `Week3_Problem1_AnB_With_IdentityProvider.anb`

Required setting (from assignment):
- instantiate `P = i` (intruder plays role `P`);
- all other roles are honest (`A`, `B`, `I`);
- show intruder can produce every outgoing message of role `P`.

Role `P` messages in this protocol:
1. `P -> A: P,B,F,T,NA`
2. `P -> B: {A,P,B,F,T,NA,Grant}inv(pk(I)),F`

---

## Initial Intruder Knowledge for Role `P=i`
From role `P` knowledge (after instantiation):
`{A,B,i,I,pk(A),pk(B),pk(i),pk(I),inv(pk(i))}`

`F,T,NA,Grant` are variables and may be left lazy until needed.

---

## Step-by-Step Lazy Intruder Derivation

### Outgoing Message 1
Target:
`i, B, F, T, NA`

Derivation:
1. `i` is in knowledge (Axiom).
2. `B` is in knowledge (Axiom).
3. `F` is a variable: keep lazy.
4. `T` is a variable: keep lazy.
5. `NA` is a variable: keep lazy.
6. Compose tuple with public concatenation operator.

So message 1 is executable.

---

### Incoming Message before Outgoing Message 2
Before message 2, role `P` receives from `A`:
`{A,i,B,F,T,NA,Grant}inv(pk(I))`

This exact signed token is now part of intruder knowledge by Axiom.

---

### Outgoing Message 2
Target:
`{A,i,B,F,T,NA,Grant}inv(pk(I)),F`

Derivation:
1. First component `{A,i,B,F,T,NA,Grant}inv(pk(I))`:
   already known from previous incoming message (Axiom).
2. Second component `F`:
   known from first message context (lazy variable choice remains valid).
3. Compose pair with public concatenation operator.

So message 2 is executable.

---

## Conclusion
Following the lazy intruder method from the lecture (Axiom + Compose + lazy variables), the intruder can generate all outgoing messages of role `P`.

Therefore, role `P` is executable under the required Week 3 instantiation.
