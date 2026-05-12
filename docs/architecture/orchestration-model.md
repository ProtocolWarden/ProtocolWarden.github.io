# Orchestration Model

OperationsCenter is the orchestration core. It consumes topology, protocol, and
governance inputs, but it does not own all of those semantics.

## Main orchestration responsibilities

- planning
- policy evaluation
- routing requests
- execution coordination
- evidence retention

## Non-responsibilities

- owning CxRP wire semantics
- owning RxP runtime invocation semantics
- owning platform topology truth
- owning deployment lifecycle
