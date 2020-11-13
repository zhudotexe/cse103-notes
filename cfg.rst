Context-Free Languages
======================
CFLs are more powerful than regular languages! You can use them to do things like balance parens.

Ex. palindromes, :math:`0^n1^n`, balanced parens, etc.

Context-Free Grammars
---------------------
CFGs are used to generate CFLs.

Definition
^^^^^^^^^^
:math:`G = (N, \Sigma, P, S)`

.. note::
    N ("nonterminals") is sometimes V ("variables"), and P ("productions") is sometimes R ("rules")

- :math:`N` is a finite set (nonterminal symbols/variables)
- :math:`\Sigma` is a finite set (terminal symbols, disjoint from N)
    - :math:`N \cap \Sigma = \emptyset`
- :math:`P` is a finite subset of :math:`N \times (N \cup \Sigma)^*`
- :math:`S \in N` is the start symbol/variable

Convention
^^^^^^^^^^

- :math:`A, B, C...` = nonterminals
- :math:`a, b, c...` = terminals
- :math:`\alpha, \beta, \gamma...` = strings in :math:`(N \cup \Sigma)^*`
- :math:`A \to \alpha` for :math:`(A, \alpha)`
- :math:`A \to \alpha_1, A \to \alpha_2, A \to \alpha_3` = :math:`A \to \alpha_1 | \alpha_2 | \alpha_3`

A grammar can be defined as a list of rules. The nonterminals can be found on the left, the rules are listed,
the terminals are the states on the right that are not on the left, and the start state is the top nonterminal.

Example
^^^^^^^

.. note::
    For these examples, :math:`\to` will be expressed as ``:=`` and :math:`\epsilon` as ``e``.

:math:`a^nb^n`

.. code-block:: text

    S := a S b | e

Ex. :math:`a^3b^3` can be ``S := aSb := aaSbb := aaaSbbb := aaabbb``.