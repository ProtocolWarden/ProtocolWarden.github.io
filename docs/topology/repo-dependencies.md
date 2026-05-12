# Repo Dependencies

Dependency direction should follow ownership boundaries:

- docs depend on public-safe knowledge surfaces
- governance depends on protocol and topology surfaces
- orchestration depends on protocols, runtime, and manifest layers
- runtime layers should not quietly own orchestration semantics
