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

Contradiction
-------------

Prove that the opposite statement causes a contradiction.

Ex. Prove that :math:`\sqrt{2}` is irrational.

1. Assume that :math:`\sqrt{2} = \frac{p}{q}, p, q \in N` with no common factor
2. :math:`p^2 = 2q^2`
3. :math:`p^2` is even
4. :math:`p` is even
5. :math:`p = 2k`
6. :math:`\sqrt{2} = \frac{2k}{q}`
7. :math:`q^2 = \frac{(2k)^2}{2} = 2k^2`
8. :math:`q^2` is even
9. :math:`q` is even
10. :math:`2 | p` and :math:`2 | q`, so by contradiction :math:`\sqrt{2}` is not rational.

Pidgeonhole Principle
---------------------

Given *n* containers and *m* items, if m > n, at least one container must have more than one item in it.

Ex. For any *m*, there exists a multiple of *m* that is a sequence of 1s followed by a sequence of 0s in binary.

- For some m, consider the sequence ``1 11 111 ... 111...11`` where the last item is of length m+1
- if you divide by m, there are only *m* remainders possible: [0..m-1]
- There are m+1 items in the sequence but only m possible remainders, so two items in the sequence will have the same remainder
- Let :math:`a = k_1m + r, b=k_2m+r, a > b`
- :math:`\therefore a-b = (k_1-k_2)m`
- :math:`a-b` is a multiple of *m* and of form ``111...00``
