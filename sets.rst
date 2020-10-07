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

**Binary Relation**

A binary relation on A and B is defined by some subset of :math:`A \times B` - some examples of binary relations on
:math:`N \times N` are:

- :math:`=`: :math:`\{(1, 1), (2, 2), ...\}`
- :math:`<`: :math:`\{(1, 2), (1, 3), (2, 3), ...\}`

This can be denoted :math:`a < b \to (a, b) \in <`

Properties
^^^^^^^^^^

.. note::

    For this notation, the symbol :math:`\sim` represents an arbitrary relation. This can also be denoted :math:`R`,
    but that doesn't look good in LaTeX.

- Reflexive: :math:`x \sim x`
    - ex: =, <=
- Symmetric: :math:`x \sim y \implies y \sim x`
    - ex: =, but *not* < or <=
- Transitive: :math:`x \sim y \land y \sim z \implies x \sim z`
    - ex: =, <, <=
    - but not: :math:`\{ (x, y) | x, y \in N \land x = y - 1\}`

If a relation has all 3 properties, it is called an *equivalence relation*

Functions
---------
A function is a binary relation defined on the cross product of the domain and the codomain.

Given 2 sets A and B, a function :math:`f` is a binary relation on :math:`A \times B` s.t.
for all x in A, there exists exactly one y in B s.t. :math:`(x, y) \in f`

Notation: :math:`f: A \to B`

Graph
-----
An undirected graph can be represented as a tuple :math:`G = (V, E)` where V and E are sets (vertices, edges),
where :math:`E \subseteq \{\{x, y\} | x, y \in V \land x \neq y\}` (set of sets of two vertices)

A digraph is similar, but E must use ordered pairs rather than sets to indicate the direction of the edge, and
an edge can go to the same vertex. :math:`E \subseteq \{(x, y) | x, y \in V \times V\}`

Ex:

.. code-block:: text

    (1) --- (2)     V = {1, 2, 3}
     |              E = {{1, 2}, {1, 3}}
    (3)

.. code-block:: text

    (1) --> (2)     V = {1, 2, 3}
     ^              E = {(1, 2), (3, 1)}
    (3)

You can use digraphs to represent relations:

.. image:: _static/graph1.png
    :width: 450

- Reflexive: every vertex has a self-loop
- Symmetric: all arrows must be bi-directional
- Transitive: the "jump" edge must exist (bottom of drawing)
