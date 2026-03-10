# Week 4 - Problem 3: Type-Flaw Resistance Check

Files checked:
- `Week4_Problem1_MainProtocol_Formats.anb`
- `Week4_Problem2_AnB_KeyLookup_Protocol.anb`

Goal (from lecture): for any two non-variable SMP terms, if they unify, they have the same type.

## 1) Format design used
Main delegation protocol uses explicit format symbols:
- `fReq(p,B,F,T,NA)`
- `fAuthProof(A,p,B,F,T,NA,h(pw(A,I),NA))`
- `fGrant(A,p,B,F,T,NA,Grant)`
- `fUse(Token,F)` where `Token = {fGrant(...)}inv(pk(I))`
- `fData(Photos)`

Key lookup protocol uses:
- `fKeyReq(A,X)`
- `fKeyResp(X,pk(X))`

Each protocol message kind has a dedicated top-level format symbol.

## 2) Why this prevents type-flaw unification
Potential unification between different message kinds would require equal top-level symbols.
That is impossible across different format constructors:
- `fReq` does not unify with `fAuthProof`, `fGrant`, `fUse`, `fData`, `fKeyReq`, or `fKeyResp`.
- `fKeyReq` does not unify with `fKeyResp`.
- Encrypted forms also remain separated by inner format type.

So only same-kind messages can unify, and those are same type by construction.

## 3) Conclusion
Under the Week 4 formatted design, message-pattern unification is type-aligned.
Therefore this model is type-flaw resistant in the intended lecture sense.
