# H003 — Statement

## Problem Binding

Can shared, stable categories (objects, spatial neighbourhoods)
arise as equilibria between observers who each choose how to
partition a common state space — without presupposing space?

Source: Forschungsprogramm Raumzeit, Schnittspiel S-1 (BR-24).

## Game (S-1)

- Players: N subsystems i = 1..N of a shared state space X
  with dynamics x(t+1) = f(x(t)).
- Moves: each player chooses a partition P_i of X
  from a finite set of admissible partitions (a "cut", AX3).
- Payoff: u_i(P_i, P_-i) = A_i - λ · K(P_i)
  - A_i: predictive accuracy of player i's next observation,
    given its own partition and the partitions of the others.
  - K(P_i) = log2 |P_i|: compression cost in bits (AX2).
  - λ > 0: cost weight.
- Solution concept: Nash equilibrium of partitions.

## Hypothesis Statement

If S-1 is played on dynamics with local interactions,
the equilibrium partitions converge on local neighbourhood
structures (a proto-spatial order),
with finer partitions for small λ and coarser ones for large λ.

## Scope

- Claim concerns the model only.
- No claim that physical spacetime is such an equilibrium.
- Transfer to physics remains a separate hypothesis (BR-24).
