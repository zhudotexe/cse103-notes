Proofs
======

*10/12/2020 -*

Definitions:

- Statements to be proved or already proved:
    - Theorem
    - Proposition
    - Lemma
    - Corollary (immediately follows from proof of theorem)
- Statements assumed to be true:
    - Axiom
    - Postulate

Induction
---------

**Weak Induction**: Prove base cases, then prove inductive steps.

Ex. Prove that the sum of the first *m* odd numbers :math:`S(m)` is equal to :math:`m^2`.

- B.S. m = 1, :math:`1 = 1^2`.
- I.S. Assume :math:`S(m) = m^2` for some :math:`m \geq 1`.
    - :math:`S(m + 1) = S(m) + 2(m+1)-1`
    - :math:`=m^2+2m+2-1`
    - :math:`=m^2+2m+1`
    - :math:`=(m+1)^2`.

**Strong Induction**: Prove all cases less than current case implies current case.

Ex. Prove :math:`\forall m > 1, m` is divisible by a prime.

Consider any :math:`m > 1`:

1. m is a prime. QED.
2. m is not a prime: :math:`m = a * b`, where :math:`a,b < m` and :math:`a, b > 1`
    1. By IH, :math:`a` is divsible by a prime :math:`P`
    2. :math:`P | a` and :math:`a | m`, so :math:`P | m`. QED.

Contrapositive
--------------

Rather than proving :math:`p \implies q`, prove :math:`\lnot q \implies \lnot p`.

Ex. :math:`p^2 \text{ is even} \implies p \text{ is even}`