DFAs Extra
==========

Minimizing a DFA
----------------
Given a DFA:

1. Remove inaccessible states
2. Collapse equivalent areas

E.g.:

.. image:: _static/dfa14.png
    :width: 500

.. image:: _static/dfa15.png
    :width: 500

.. image:: _static/dfa16.png
    :width: 500

Identifying Equivalent States
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Do this by identifying all states that cannot be equivalent: two states cannot be equivalent if processing
the same some string at each state brings you to a different acceptance value

.. image:: _static/dfa17.png
    :width: 500

Formally, :math:`p \approx q \text{ iff } \forall x \in \Sigma^* (\hat{\delta}(p, x) \in F \iff \hat{\delta}(q, x) \in F)`

.. image:: _static/dfa18.png
    :width: 500

You can use these equivalence classes to make a quotient automaton:

.. image:: _static/dfa19.png
    :width: 500

Equivalence Relations
^^^^^^^^^^^^^^^^^^^^^

- must be reflexive, symmetric, transitive
- partitions a set into disjoint parts (equivalence classes)
    - if R is an equivalence relation on A, :math:`[x]_R = \{ y | x\ R\ y \}`
- given :math:`[x]_R` and :math:`[y]_R`, they are either the same or disjoint
- the union of all equivalence classes of a set is the set
- the *index* of an equivalence relation is the number of equivalence classes

If, for all :math:`x \in A, [x]_1 \subseteq [x]_2` (where 1 and 2 are 2 different relations), then 1 is *finer* than 2.

Therefore, the index of relation 1 will be greater than the index of relation 2.

.. image:: _static/dfa20.png
    :width: 350

Myhill-Nerode
-------------
Idea:

- Let L be any language in :math:`\Sigma^*` (so :math:`L \subseteq \Sigma^*`).
- Let :math:`R_L` be a special equivalence relation on :math:`\Sigma^*`.
- :math:`x\ R_L\ y` iff :math:`\forall z \in L,\ (xz \in L \iff yz \in L)`
    - these two strings are equivalent if regardless of what you append to them, they are both either in the language or not

**Thm**:

Let :math:`L \subseteq \Sigma^*`. Then the following statements are equivalent:

1. L is regular
2. The index of :math:`R_L` is finite

:math:`1 \implies 2` is relatively easy to prove - :math:`2 \implies 1` (shown here) is harder, but we prove it by
constructing a DFA:

.. image:: _static/dfa21.png
    :width: 350

If you can find an infinite sized set of all strings in :math:`\Sigma^*` such that no two of them are in the same
equivalence class, then that language is not regular (since the equivalences classes of that set are a subset of
equivalence classes in that language):

.. image:: _static/dfa22.png
    :width: 350


**Ex.**

Prove that :math:`L = \{ 0^n 1^n | n \geq 1 \}` is not regular using M-N:

- Let :math:`S = \{ 0^n | n \geq 1 \}`
- :math:`|S|` is infinite
- Examine :math:`0^i, 0^j \in S` where :math:`i \neq j`
    - By appending :math:`1^i` to both strings, we get one string in the language and another that is not
    - so all items in this set are in different equivalence classes of :math:`R_L`
- So the language is not regular.

**Ex.**

Prove that :math:`L = \{ w \in \Sigma^* | \text{w is a palindrome} \}` is not regular using M-N:

- Let :math:`S = \{ 01, 001, 0001, ... \} = \{ 0^i1 | i \geq 1 \}`
- :math:`|S|` is infinite
- Examine :math:`0^i1, 0^j1 \in S` where :math:`i \neq j`
    - By appending :math:`0^i` to both strings, we get one string in the language and another that is not
    - so all items in this set are in different equivalence classes of :math:`R_L`
- So the language is not regular.

**Ex.**

:math:`L = \{ ww | w \in \Sigma^* \}`

- Let :math:`S = \{ 0^i1 | i \geq 1 \}`
- :math:`|S|` is infinite
- Examine :math:`0^i1, 0^j1` where :math:`i \neq j`
    - By appending :math:`0^i1` to both strings, we get one string in the language and another that is not:
        - :math:`0^i10^i1 \in L`
        - :math:`0^j10^i1 \notin L`
    - so all items in this set are in different equivalence classes of :math:`R_L`
    - so the index of :math:`R_L` is infinite
- So the language is not regular.

**Ex.**

:math:`L = \{ 1^{m!} | m \geq 1 \}`

- Let :math:`S = L`
- :math:`|S|` is infinite
- Examine :math:`1^{i!}, 1^{j!}` where :math:`i \neq j`
    - By appending :math:`1^{ii!}`, we get:
    - :math:`1^{i!}1^{ii!} = 1^{(i+1)!} \in L`
    - :math:`1^{j!}1^{ii!} = 1^{\frac{j!}{i!}i! + ii!}`
        - :math:`= 1^{i!(\frac{j!}{i!} + i)}`
        - proof by contradiction: assume :math:`i!(\frac{j!}{i!} + i)` is some factorial :math:`q!`
            - :math:`q! = i!(\frac{j!}{i!} + i)`
            - :math:`q(q-1)...(i+1) = \frac{j!}{i!} + i`
            - :math:`= j(j-1)...(i+1)+i`
            - dividing both sides by :math:`i+1`, the remainder on the left is 0 while the remainder on the right is 1
            - so :math:`i!(\frac{j!}{i!} + i)` is not some factorial.
        - so :math:`= 1^{i!(\frac{j!}{i!} + i)} \notin L`
    - so all items in this set are in different equivalence classes of :math:`R_L`
    - so the index of :math:`R_L` is infinite
- so the language is not regular.

**Ex.**

:math:`L = \{ a^ib^jk^c | i,j,k \geq 0 \land i = 1 \implies j = k \}`

This language cannot be proven irregular using the pumping lemma thm.

- let :math:`S = \{ ab^i | i \geq 1 \}`
- :math:`|S|` is infinite
- Examine :math:`ab^i, ab^j` where :math:`i \neq j`. Append :math:`c^i` to both:
    - :math:`ab^ic^i \in L`
    - :math:`ab^jc^i \notin L`
- so the index of :math:`R_L` is infinite and L is not regular.

**Ex.**

:math:`L = \{ 0^p | p \text{ is prime}\}`

.. image:: _static/dfaext1.png
    :width: 350

