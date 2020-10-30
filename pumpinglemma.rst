Pumping Lemma
=============

If a language L is regular, then:

**(P)**: There exists a :math:`p \geq 0` s.t. for any string :math:`s \in L` with :math:`|s| \geq p`, there exist
strings :math:`xyz` s.t. :math:`s = xyz, y \neq \epsilon, |xy| \leq p`, and for all :math:`i \geq 0`, the
string :math:`xy^iz \in L`.

"there exists a non-empty string (y) within the first *p* characters (3rd constraint) that can be pumped,
with the resulting string still being in the language."

The contrapositive of this (:math:`\lnot P \implies` L is not regular) is used to prove that a language is not regular.


**(not P)**: For all :math:`p \geq 0` there exists a string :math:`s \in L` with :math:`|s| \geq p`, and for all
:math:`x, y, z` such that :math:`xyz = s, y \neq \epsilon, |xy| \leq p` there exists an :math:`i \geq 0` such that
:math:`xy^iz \notin L`.

You can use this adversarial game to prove the contrapositive:

.. image:: _static/pumping1.png
    :width: 500

Examples
--------

Ex 1
^^^^

:math:`A = \{ 0^m1^m | m \geq 0 \}` is not regular.

Use the demon game as a valid proof:

- Demon picks *p*
- we pick :math:`s \in L` and :math:`|s| \geq p`
    - :math:`s = 0^p1^p`
- demon picks partition :math:`x, y, z` s.t. :math:`xyz = s, |xy| \leq p, y \neq \epsilon`
- we show any partition that satisfies these conditions cannot be pumped for some :math:`i \geq 0`
    - since :math:`|xy| \leq p, y \neq \epsilon` and we chose :math:`s = 0^p1^p`, *y* must be one or more 0s
    - choose :math:`i = 2`: this causes :math:`xy^2z` to have more 0s than 1s and not be in the language
    - QED

Ex 2
^^^^

:math:`L = \{ w | \text{ # of 0s = # of 1s} \}` is not regular.

Abbreviated demon argument:

- :math:`p`
- :math:`s = 0^p 1^p`
- for any partition :math:`x, y, z` s.t. :math:`xyz = s, |xy| \leq p, y \neq \epsilon`: (same argument as before)
    - *y* must be made of 1 or more 0s
    - choose :math:`i = 2`: this causes :math:`xy^2z` to have more 0s than 1s and not be in the language
    - QED

Ex 3
^^^^

:math:`L = \{ 1^j 0^i | j < i \}` is not regular

- :math:`p`
- :math:`s = 1^p 0^{p+1}` (conditions: :math:`s \in L, |s| = 2p+1 \geq p`)
- for any partition :math:`x, y, z` s.t. :math:`xyz = s, |xy| \leq p, y \neq \epsilon`:
    - *y* must be made of 1 or more 1s
    - choose :math:`i = 2`: this causes :math:`xy^2z` to have :math:`i \geq j` and not be in the language
    - QED

Ex 4
^^^^
:math:`L = \{ 0^i 1^j | i > j \}` is not regular

- Assume L is regular
- so the reverse of L is regular (closure under reverse)
- The reverse of L is not regular (ex 3)
- so L is not regular. QED.

Proof
-----

