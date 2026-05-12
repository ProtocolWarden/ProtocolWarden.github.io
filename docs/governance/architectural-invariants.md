# Architectural Invariants

Examples of important invariants:

- protocol repos own canonical protocol semantics
- manifest repos own topology and visibility truth
- public outputs are safe projections, not independent drift copies
- unknown visibility fails closed
- orchestrators consume, but do not absorb, protocol or topology ownership
