Context-Free Languages
======================
CFLs are more powerful than regular languages! You can use them to do things like balance parens.

Ex. palindromes, :math:`0^n1^n`, balanced parens, etc.

**Context-Free Grammars**

CFGs are used to generate CFLs.

Definition
----------
:math:`G = (N, \Sigma, P, S)`

.. note::
    N ("nonterminals") is sometimes V ("variables"), and P ("productions") is sometimes R ("rules")

- :math:`N` is a finite set (nonterminal symbols/variables)
- :math:`\Sigma` is a finite set (terminal symbols, disjoint from N)
    - :math:`N \cap \Sigma = \emptyset`
- :math:`P` is a finite subset of :math:`N \times (N \cup \Sigma)^*` (productions)
- :math:`S \in N` is the start symbol/variable

Convention
----------

- :math:`A, B, C...` = nonterminals
- :math:`a, b, c...` = terminals
- :math:`\alpha, \beta, \gamma...` = strings in :math:`(N \cup \Sigma)^*`
- :math:`A \to \alpha` for :math:`(A, \alpha)`
- :math:`A \to \alpha_1, A \to \alpha_2, A \to \alpha_3` = :math:`A \to \alpha_1 | \alpha_2 | \alpha_3`

A grammar can be abbreviated as a list of rules. The nonterminals can be found on the left, the rules are listed,
the terminals are the states on the right that are not on the left, and the start state is the top nonterminal.

Examples
--------

.. note::
    For these examples, :math:`\to` will be expressed as ``:=`` and :math:`\epsilon` as ``e``.

Ex 1
^^^^

:math:`a^nb^n`

Formally:

- :math:`G = (N, \Sigma, P, S)`
- :math:`N = \{S\}`
- :math:`\Sigma = \{a, b\}`
- :math:`P = \{S \to aSb, S \to \epsilon\}`
- :math:`S = S`

Abbreviated:

.. code-block:: text

    S := a S b | e

Ex. :math:`a^3b^3` can be ``S := aSb := aaSbb := aaaSbbb := aaabbb``.

Ex 2
^^^^
Even length palindromes.

.. code-block:: text

    S := a S a | b S b | e

Ex. ``aabbaa`` can be ``S := aSa := aaSaa := aabSbaa := aabbaa``.

Ex 3
^^^^
Odd length palindromes.

.. code-block:: text

    S := a S a | b S b | a | b

Ex. ``aababaa`` can be ``S := aSa := aaSaa := aabSbaa := aababaa``.

Ex 4
^^^^
The set of strings over ``{a, b}`` such that the reversal of a string is the string with a's and b's swapped

.. code-block:: text

    S := a S b | b S a | e

Ex 5
^^^^
The set of even length strings

.. code-block:: text

    S := a T | b T | e
    T := a S | b S

    OR

    S := aaS | abS | baS | bbS | e

Ex 6
^^^^
Even length with two middle symbols the same

.. code-block:: text

    S := a S a | a S b | b S a | b S b | aa | bb

Ex 7
^^^^
Odd length with first, middle, and last symbols the same

.. code-block:: text

    S := a T a | b U b
    T := a T a | a T b | b T a | b T b | a
    U := a U a | a U b | b U a | b U b | b

Ex 8
^^^^
Equal number of a's and b's

.. code-block:: text

    S := a S b | b S a | S S | e

Ex 9
^^^^
Palindromes

.. code-block:: text

    S := a S a | b S b | a | b | e

Ex 10
^^^^^
Balanced parentheses

.. code-block:: text

    S := ( S ) | S S | e

Ex 11
^^^^^
:math:`\{0, 1\}^*`

.. code-block:: text

    S := 0 S | 1 S | e

Special Constructions
---------------------

- Right Linear
    - ``A := x B | x`` where :math:`x \in \Sigma^*`
- Strongly Right Linear
    - ``A := x B | e`` where :math:`x \in \Sigma`
- Left/Strongly Left Linear are similar.
    - All the linear constructions generate the regular languages!

DFA Relation
^^^^^^^^^^^^
Since the linear constructions generate the regular languages, they must have an associated DFA:

:math:`M = (Q, \Sigma, \delta, s, F)`

- Make a variable for each state: :math:`V = \{V_i | q_i \in Q\}`
- :math:`\Sigma = \Sigma`
- For each :math:`\delta(q_i, a) \to q_j` where :math:`a \in \Sigma`:
    - make a rule :math:`V_i \to a V_j`
- For each :math:`q_i \in F`:
    - make a rule :math:`V_i \to \epsilon`
- :math:`S = V_0`

**Ex.** Use this method on the language of an odd number of 0s, even number of 1s.

.. image:: _static/cfg1.png
    :width: 350

.. code-block:: text

    V1 := 0 V2 | 1 V4
    V2 := 0 V1 | 1 V3 | e
    V3 := 0 V4 | 1 V2
    V4 := 0 V3 | 1 V1

Closure
-------

Given:

- :math:`G_1 = (N_1, \Sigma, P_1, S_1)`
- :math:`G_2 = (N_2, \Sigma, P_2, S_2)`

Union
^^^^^

- :math:`G = (N, \Sigma, P, S)`
- :math:`N = N_1 \cup N_2 \cup \{S\}`
- :math:`P = P_1 \cup P_2 \cup \{S \to S_1, S \to S_2\}`
- :math:`S = S`

Concatenation
^^^^^^^^^^^^^
- :math:`G = (N, \Sigma, P, S)`
- :math:`N = N_1 \cup N_2 \cup \{S\}`
- :math:`P = P_1 \cup P_2 \cup \{S \to S_1 S_2\}`
- :math:`S = S`

Kleene Star
^^^^^^^^^^^
(Examining :math:`G_1^*`)

- :math:`G = (N, \Sigma, P, S)`
- :math:`N = N_1 \cup \{S\}`
- :math:`P = P_1 \cup \{S \to \epsilon, S \to S_1S\}`
- :math:`S = S`

Intersection (Not)
^^^^^^^^^^^^^^^^^^
CFLs are *not* closed under intersection! Counterexample:

- :math:`a^nb^nc^n` is not a CFL
- :math:`\{a^mb^mc^n | m,n \geq 0\}` is a CFL
    - Pf: See CFG 1 below
- :math:`\{a^mb^nc^n | m,n \geq 0\}` is a CFL
    - Pf: See CFG 2 below
- :math:`\{a^mb^nc^n | m,n \geq 0\} \cap \{a^mb^mc^n | m,n \geq 0\} = a^nb^nc^n` which is not a CFL.

.. code-block:: text

    CFG 1
    S := A B
    A := a A b | e
    B := c B   | e

    CFG 2
    S := A B
    A := a A   | e
    B := b B c | e

Chomsky Normal Form
-------------------
A special form where all rules are of the form ``A := BC | a`` (where :math:`A, B, C \in N` and :math:`a \in \Sigma`).

**Thm**. For any CFG G, there is a CFG G' in CNF s.t. :math:`L(G')=L(G) - \epsilon`.

Converting to CNF
^^^^^^^^^^^^^^^^^

Step 1: Get rid of epsilon-rules and unit-rules

.. image:: _static/cfg2.png
    :width: 750

Step 2: Make everything either go to one terminal or multiple nonterminals

.. image:: _static/cfg3.png
    :width: 750

Step 3: Make every run of 2+ nonterminals just 2 nonterminals.

.. image:: _static/cfg4.png
    :width: 750

**Ex**.

:math:`L = \{a^nb^n | n \geq 1\}`

.. code-block:: text

    0.
    S := a S b | e

    1. add S := a b
    S := a S b | e | a b

    2. Remove e-productions
    S := a S b | a b

    3. Give each terminal a nonterminal
    S := a S b | a b
    A := a
    B := b

    4. Replace nonterminals on the right
    S := A S B | A B
    A := a
    B := b

    5. Replace >2 nonterminals
    S  := A S2 | A B
    S2 := S B
    A  := a
    B  := b

**Ex**.

Balanced parentheses.

.. code-block:: text

    0.
    S := ( S ) | S S | e

    1. add S := ( ) and remove epsilon
    S := ( S ) | S S | ( )

    2. make each terminal a nonterminal
    S := A S B | S S | A B
    A := (
    B := )

    3. Replace runs of >2 nonterminals
    S  := A S2 | S S | A B
    S2 := S B
    A  := (
    B  := )

A more complex example can be found
`on Canvas <https://canvas.ucsc.edu/courses/36492/files/folder/Handouts?preview=2700149>`_.

Pumping Lemma for CFLs
----------------------
For every CFL L, there exists a :math:`p \geq 0` s.t. every :math:`z \in L` of length :math:`\geq p` can be
divided into *five* substrings :math:`z = uvwxy` such that :math:`vx \neq \epsilon` and :math:`|vwx| \leq p`,
and for all :math:`i \geq 0`, :math:`uv^iwx^iy \in L`.

In English: every sufficiently long string can be divided into 5 segements such that the middle 3 are not too
long, and the second and fourth are both not empty, and no matter how much you pump the 2nd and 4th (simultaneously),
the string stays in the language.

.. cfg5

We can use this to prove that a language is not a CFL. We just need to show:

- for all :math:`p \geq 0`
- there exists :math:`s \in L` of length at least :math:`p`
- such that for all :math:`uvwxy` with :math:`z = uvwxy, vx\neq \epsilon, |vwx| \leq p`
- there exists :math:`i` 
- such that :math:`uv^iwx^iy \notin L`.

We can use the adversary game again.

Ex 1
^^^^

:math:`L = \{a^nb^nc^n | n \geq 0\}`

- :math:`p`
- :math:`s = a^pb^pc^p`, :math:`s \in L, |s| = 3p > p`.
- :math:`uvwxy = a^pb^pc^p`, :math:`|vwx| \leq p, vx \neq \epsilon`
- Let :math:`i=2`
- Case 1: :math:`vwx` is entirely contained within :math:`a^p, b^p, \text{ or } c^p`.
    - Either *v*, *x*, or both must be made entirely of a's, b's, or c's
    - Pumping that fragment results in more of that letter than the others, and the resulting string is not in the language
- Case 2: Either *v* or *x* falls on a boundary between letters
    - Pumping that fragment would result in a mixture of letters, and the resulting string is not in the language
- Case 3: *v* and *x* are made of two different letters (*w* falls on the boundary)
    - Pumping those fragments would result in less of the letter that did not contain *v* or *x*, and the resulting string is not in the language.

.. image:: _static/cfg6.png
    :width: 350

Ex 2
^^^^

:math:`L = \{a^nb^na^n | n \geq 0\}`

- :math:`p`
- :math:`s = a^pb^pa^p`: :math:`s \in L, |s| = 3p > p`.
- :math:`uvwxy = a^pb^pa^p`: :math:`|vwx| \leq p, vx \neq \epsilon`
- Let :math:`i=2`
- Case 1: :math:`vwx` is entirely contained within :math:`a^p` or :math:`b^p`
    - Either *v*, *x*, or both must be made entirely of a's or b's
    - Pumping that fragment results in more of that letter than the others, and the resulting string is not in the language
- Case 2: Either *v* or *x* falls on a boundary between letters
    - So *v* or *x* contains both a's and b's
    - Pumping that fragment would result in a mixture of letters, and the resulting string is not in the language
- Case 3: *v* and *x* are made of two different letters (*w* falls on the boundary)
    - Pumping those fragments would result in less a's in the section that did not contain *v* or *x*, and the resulting string is not in the language.

Ex 3
^^^^

:math:`\Sigma = \{0, 1\}; L = \{ww | w \in \Sigma^* \}`

- :math:`p`
- :math:`s = 0^p1^p0^p1^p`: :math:`s \in L, |s| = 4p > p`.
- :math:`uvwxy = 0^p1^p0^p1^p`: :math:`|vwx| \leq p, vx \neq \epsilon`
- Case 1: :math:`vwx` is entirely on one half of the string
    - Let :math:`i=2`
    - By pumping, at least one symbol on the boundary is pushed over the boundary to the other half
        - Which means that either the second half would start with 1 (but the first starts with 0!)
        - Or the first half ends with 0 (but the second ends with 1!)
    - the resulting string is not in the language.
- Case 2: *v* and *x* are on opposite halves (*w* is on the boundary)
    - let :math:`i=0`
    - The new string becomes :math:`0^p1^a0^b1^p`
    - Both *a* and *b* cannot both be *p*, since either :math:`a < p` or :math:`b < p`
    - So the resulting string is not in the language

(...what about the boundary?)

Ex 4
^^^^
(same language as ex 3)

:math:`\Sigma = \{a, b\}; D = \{ww | w \in \Sigma^* \}`

Important note: CFL :math:`\cap` CFL is not necessarily a CFL, but CFL :math:`\cap` regular language is

Consider :math:`D' = D \cap L(a^*b^*a^*b^*) = \{a^nb^ma^nb^m | n, m \geq 0 \}`

- Assume *D* is a CFL
- then *D'* must be (since the intersection of a CFL and a regular language is a CFL)
- however *D'* is not a CFL:
- :math:`p`
- :math:`s = a^p b^p a^p b^p`: :math:`s \in L, |s| = 4p > p`.
- :math:`uvwxy = a^p b^p a^p b^p`: :math:`|vwx| \leq p, vx \neq \epsilon`
- Let :math:`i=2`
- Case 1: *v* or *x* crosses a boundary between a's and b's
    - By pumping this fragment, the resulting string introduces a mixture
    - no longer of the form :math:`a^nb^ma^nb^m`
- Case 2: :math:`vwx` is entirely contained within one section of a's or b's
    - By pumping this fragment, this changes the number of a's or b's on only one side
    - so the string is not longer in the language
- Case 3: *v* and *x* are made entirely of different letters (*w* contains the boundary)
    - Case 1: the boundary is the middle of the left section
        - By pumping this fragment, this changes the number of a's, b's, or both on only one side
        - so the string is not longer in the language
    - Case 2: the boundary is the center
        - By pumping this fragment, this changes the number of b's on the left but not the right, a's on the right but not the left, or both
        - so the string is not longer in the language
- so *D* is not a CFL.

Ex 5
^^^^

:math:`\Sigma = \{a, b\}; L = \{x \in \Sigma^* | x \text{ is not of form } ww, w \in \Sigma^* \}`

L *is* a CFL!

- Odd length strings are certainly not of this form
- what about even length ones? let :math:`L = a | b`, they must be the form :math:`L^n a L^m L^n b L^m`
    - the (n+1)th symbol on the left is different from the (n+1)th symbol on the right
    - so at least 1 symbol must not match
    - note: :math:`L^n a L^m L^n b L^m = L^n a L^{m+n} b L^m = L^n a L^n L^m b L^m`

.. code-block:: text

    S := A | B | A B | B A
    A := L A L | a          # odd length strings with a in middle
    B := L B L | b          # odd length strings with b in middle
    L := a | b
