Push-Down Automata
==================
PDAs give us a form of memory by introducing a stack, which has infinite space but containing a finite number of
elements:

.. image:: _static/pda1.png
    :width: 500

Formal Definition
-----------------

:math:`M = (Q, \Sigma, \Gamma, \delta, s, F)` where

- :math:`Q` is a finite set of states
- :math:`\Sigma` is a finite set (symbols - input alphabet)
- :math:`\Gamma` is a finite set (symbols - stack alphabet)
- :math:`\delta: (Q \times (\Sigma \cup \{ \epsilon \}) \times (\Gamma  \cup \{ \epsilon \})) \to P(Q \times (\Gamma  \cup \{ \epsilon \}))`
    - Takes a state, maybe something from the input, maybe something from the stack (popped)
    - Produces some subset of states (non-deterministic) and something to push on stack, optionally
- :math:`s \in Q` is the start state
- :math:`F \subset Q` is the accept states

Ex 1
^^^^

- :math:`L = \{ 0^n 1^n | n \geq 0 \}`
- :math:`Q = \{q_1, q_2, q_3, q_4\}`
- :math:`\Sigma = \{0, 1\}`
- :math:`\Gamma = \{ \hat{0}, $ \}`
- :math:`s = q_1`
- :math:`F = \{ q_1, q_4 \}`
- :math:`\delta` is represented by this state diagram:
- Design: Push 0s onto the stack, pop an equal number of 1s.

.. image:: _static/pda2.png
    :width: 500

:math:`x, y \to z` represents whether to read, what to pop, and what to push, if any.

.. image:: _static/pda3.png
    :width: 500

Ex 2
^^^^

:math:`L = \{ w w^R | w \in \{0, 1\}^* \}`

.. image:: _static/pda4.png
    :width: 500

.. note::
    The transition :math:`q_2 \to q_3` is nondeterministic and can be an epsilon move.

Ex 3
^^^^

The complement of :math:`L = \{ w w | w \in \{0, 1\}^* \}` (see CFG ex. 5)

.. image:: _static/pda5.png
    :width: 750

