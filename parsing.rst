Parsing
=======

Example: Propositional Logic

- Variable: P, Q, R, ...
- Constants: T/F, 0/1, etc.
- Binary operations: :math:`\land, \lor, \implies, \iff`
- Unary operations: :math:`\lnot`
- Parentheses

.. code-block:: text

    E := ( E B E ) | ( U E ) | C | V
    B := V | ^ | => | <=>
    U := ~
    C := 0 | 1
    V := P | Q | R | ... | Z

Let's parse: :math:`(((P \lor Q) \land R) \lor (Q \land (\lnot P)))`

.. image:: _static/parsing1.png
    :width: 500


A *simple* parser algorithm (not really robust, or working for other grammars):

- Init stack with :math:`\bot`
- Scan left to right
- If open paren, push
- If operator, push
- If constant, push pointer to it
- If variable, lookup in symbol table, push pointer to it
- If close paren, reduce:
    - Allocate storage for node in expression tree
    - Pop object (ptr to right operand, could be const, var, or another node)
    - Pop object (should be the operator), save in node
    - If operator is binary:
        - Pop object (ptr to left operand)
    - Pop object (should be left paren)
    - Push pointer to new node

.. image:: _static/parsing2.png
    :width: 500

.. image:: _static/parsing3.png
    :width: 500

.. image:: _static/parsing4.png
    :width: 500

.. image:: _static/parsing5.png
    :width: 500