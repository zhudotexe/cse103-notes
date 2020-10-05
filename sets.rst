Sets
====

*10/5/2020 -*

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

Definition:

- :math:`\{ x \in N | \frac{x}{2} \in N \}` - even number definition by restricted comprehension
- :math:`\{ x | P(x) \}` - unrestricted comprehension

Russel's Paradox
----------------

**Extraordinary Sets**: All sets that include themselves as an element (ex. the set of everything that is not a teacup)

**Ordinary Sets**: All sets that don't have themselves as a member

Paradox: Does the set of all ordinary sets contain itself?

This is a paradox - which means that the set of all sets cannot exist

Relations
---------

Ex. :math:`<` - the set of all ordered pairs :math:`(a, b)` s.t. :math:`a < b`

- Cartesian product of 2 sets A, B: :math:`\{ (a, b) | a \in A \land b \in B \}`
    - e.g. :math:`\{c, d\} \times \{1, 2, 3\} = \{(c, 1), (c, 2), (c, 3), (d, 1), (d, 2), (d, 3)\}`