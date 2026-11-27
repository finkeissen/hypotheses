# H004 — Statement

## Problem Binding

Can the space of problems and their causes, generated from LLM model
knowledge alone, reach a measurable saturation point — and can that
saturation be detected by a fixed semantic-novelty threshold?

## Hypothesis Statement

For a problem-cause matrix populated from model knowledge, the share of
semantically novel atoms per major field — defined as atoms whose
nearest-neighbour cosine (embedding: bge-m3, 1024 dimensions) to the stock
that existed *before* the field was populated is below 0.80 — falls
**below 0.70 in most major fields** once breadth production has run.

Operationalization:

- novelty measure: fixed sample per pilot area, nearest neighbour against
  the pre-existing stock
- the 0.70 share is a documented *set* decision (like any cut), not an
  empirically derived constant; the resulting decision is stable for cut
  values 0.69–0.76 (measured)

## Scope

- Domain: matrix breadth production, 70 English practice fields,
  pilot measurement 2026-11-13/14
- Each major field measured through ONE pilot area (restriction;
  see falsification)
