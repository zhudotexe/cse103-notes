Regular Expressions
===================

Regular expressions over alphabet :math:`\Sigma`:

.. image:: _static/regex1.png
    :width: 350

.. image:: _static/regex2.png
    :width: 350

Ex. Begin with 0, end with 11: ``0(0+1)*11``

Ex. Contains at least 2 1s: ``(0+1)* 1 (0+1)* 1 (0+1)*`` or ``0* 1 0* 1 (0+1)*``

.. note::
    ``a+`` is often used as an abbreviation for ``aa*``

Ex. Contains the substring ``111``: ``(0+1)* 111 (0+1)*``

Ex. Even length: ``((0+1)(0+1))*``

Ex. Odd length: ``(0+1)((0+1)(0+1))*``

Ex. Strings that don't end with ``01``: ``e + 1 + (0+1)*0 + (o+1)*11`` - it's hard to exclude things!

Ex. Every 0 is followed by at least one 1: ``1* (011*)*``

Ex. 3rd symbol from right is 1: ``(0+1)* 1 (0+1)(0+1)``

Kleene's Thm
------------

For every regular expression, there is an equivalent :math:`\epsilon`-NFA.

Use strong induction to prove:

.. image:: _static/regex3.png
    :width: 350