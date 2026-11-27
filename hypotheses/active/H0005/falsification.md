# H005 — Falsification

## Refutation condition

Refuted if, within the same domain, the median best-neighbour cosine of
source-derived atoms is greater than or equal to that of model-derived atoms
(no novelty advantage), or if the advantage lies within the confidence
interval of the measurement.

## Test design (required before any confirming claim)

1. Pick a domain with BOTH atom families present (source-derived and
   model-derived), produced under comparable conditions.
2. Compute nearest-neighbour cosine for both families against the same
   reference stock (the stock that predates the domain).
3. Compare medians with interval (cluster-aware; atoms within a field are
   not independent draws); pre-register the sample size.
4. Never compare a source domain against a model domain (confounder).

## Status

Not yet measured — the test itself is an open task. H005 is stated so that
the program cannot silently treat source atoms as "newer" without the
measurement.
