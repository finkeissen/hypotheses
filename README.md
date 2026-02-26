# hypotheses

Versioned, referencable, **empirically or logically decidable** hypotheses  
as a bridge between the epistemic core and the structured knowledge matrix.

## Purpose of this repository

This repository contains **exclusively declarative, testable hypotheses** derived from or anchored in the epistemic core (`research-program`).

It serves as:

- an explicit, versionable collection of directed claims
- a reference point for the matrix (`matrix`) and the instantiations (`predictions`)
- a visible expression of the falsifiability principle (Popper-conform)

**Important:**  
There are **no** operationalized models, no code, no forecasts, no empirical data, and no fitting results here.  
→ see `predictions` for traceable projections and evaluations

## Architectural embedding (as of February 2026)

Current layer ordering:

0. Legacy                ← dismissed / unresolved / pre-formal  
1. research-program      ← epistemic core, hard core, meta-rules  
2. **hypotheses**        ← testable, falsifiable claims (this repository)  
3. matrix                ← structured, admissible knowledge representation  
4. predictions ← traceable projections, consequence maps, evaluations

Flow: Kernel → Hypotheses → Matrix → Instantiations  
Feedback: spiral model with explicit lifecycle & admissibility rules

→ Full documentation: [ARCHITECTURE.md](../research-program/blob/main/ARCHITECTURE.md) (or in the profile README)

## Principles

- Each hypothesis receives a stable ID: `H001`, `H002`, …  
- Each hypothesis **must** contain explicit falsification conditions (empirically or logically decidable)  
- **Versioning**:
  - Major (e.g. H017 → H018): change of the logical statement / semantic core
  - Minor (e.g. H017-v1 → H017-v2): addition / refinement of falsification conditions or operationalization
  - Patch (e.g. H017-v1.0 → H017-v1.1): linguistic clarification, typo fixes, format adjustments
- Falsified hypotheses are **not deleted**, but set to status `falsified`  
- Hypotheses must **not** contain implicit ontological assumptions not explicitly permitted in the core  
- All hypotheses must be **admissible** (no illegitimate transfers, no categorical errors)

→ Detailed lifecycle rules: [HYPOTHESES-LIFECYCLE.md](../research-program/blob/main/HYPOTHESES-LIFECYCLE.md)

## Folder structure (current)

hypotheses/
├── README.md  
├── index.md                  ← central overview / list of all hypotheses  
├── H001/  
│   ├── statement.md  
│   ├── falsification.md  
│   ├── evidence-trace.md  
│   └── references.yaml  
├── H002/  
└── schema/                   ← optional JSON/YAML schema for hypothesis format

## How to contribute / review

1. Clone / reference a hypothesis: `H127`  
2. Read the falsification condition → is it in principle decidable?  
3. Check against admissibility rules (MMS)  
4. In case of ambiguity / contradiction: open an issue or propose a spiral iteration

## License

CC BY-NC 4.0  
Non-commercial. Commercial use or derivatives require a separate agreement.

## Related repositories

- [research-program](https://github.com/finkeissen/research-program) – epistemic core  
- [mms](https://github.com/finkeissen/mms) – normative evaluation engine  
- [matrix](https://github.com/finkeissen/matrix) – structured knowledge representation  
- [predictions](https://github.com/finkeissen/predictions) – traceable projections & evaluations  
- [legacy](https://github.com/finkeissen/legacy) – dismissed / unresolved candidates

---

This repository is **not a truth generator**, but an **epistemic integrity filter**.

## Role in the epistemic flow

Hypotheses translate admissible structure from the research-program into directed, falsifiable claims.

They do not represent knowledge yet.
They represent epistemically constrained possibility.

Outcomes may include:
- transition into Matrix structure,
- refinement,
- falsification,
- STOP and regression to Legacy.

## Hypothesis lifecycle across layers

A hypothesis may:
- emerge from admissible structure,
- stabilize through Matrix integration,
- generate projections in Predictions,
- be falsified,
- or trigger STOP when admissibility collapses.

Lifecycle states are preserved rather than erased.

## Interfaces

- Research Program → defines admissible forms of claims
- Hypotheses → express directed, falsifiable statements
- Matrix → records structural stabilization of hypotheses
- Predictions → operationalize consequences and tests
- Legacy → preserves unresolved or inadmissible claims

## STOP vs falsification

Falsification concerns empirical or logical failure of a claim.

STOP concerns admissibility failure:
the hypothesis cannot be meaningfully evaluated under the current epistemic constraints.

Both states are preserved.

## External orientation

This repository marks the transition from epistemic rules to scientific claims.
Its effects become visible in Matrix structure and Predictions evaluation.


