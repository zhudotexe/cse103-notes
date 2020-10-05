Sets
====

**Set**: A collection of distinguishable objects, with unordered, non-repeating elements

Two sets are equal if their elements are equal

Notation
--------

- :math:`z \in S` - element member
- :math:`S = \{1, 2, 3\}` - complete denotation
- :math:`\emptyset` - empty set
- :math:`Z` - integers
- :math:`R` - real numbers
- :math:`N` - natural numbers (no 0)
- :math:`Q` - rational numbers
- :math:`A \subseteq B` - all elements in A are in B (subset)
    - :math:`\forall x, x \in A \to x \in B`
- :math:`A \cap B` - all elements in A and B (intersection)
    - :math:`\{x: x \in A \land x \in B\}`
- :math:`A \cup B` - all elements in A or B (union)
    - :math:`\{x: x \in A \lor x \in B\}`
- :math:`A - B` - all elements in A but not B (difference)
    - :math:`\{x: x \in A \land x \notin B\}`
- :math:`A \Delta B` - all elements in exactly one set (symmetric difference)
    - :math:`\{x: x \in (A - B) \lor x \in (B - A) \}`

Given a universe of discourse :math:`\Omega`:

- :math:`\bar{A} = \Omega - A` - all elements not in A (complement)

Demorgan's Laws:

- :math:`\overline{A \cap B} = \bar{A} \cup \bar{B}`
- :math:`\overline{A \cup B} = \bar{A} \cap \bar{B}`
