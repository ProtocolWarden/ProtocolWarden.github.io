# Ontology vs Topology vs Topography

This page keeps three similar words separate.

## Ontology

Ontology answers: what exists, and what does it mean?

Examples:

- repo kinds
- execution objects
- governance objects
- capability sets
- contract terms

RepoGraph owns the canonical ontology vocabulary.

## Topology

Topology answers: how are the things connected?

Examples:

- manifest consumption
- projection publication
- artifact reads and writes
- orchestration dispatch
- runtime invocation

RepoGraph owns the canonical topology vocabulary. Consumers import it; they do
not redefine it.

## Topography

Topography answers: what does the operational terrain look like in a concrete
environment?

Examples:

- local paths
- ports
- compose files
- env overlays
- machine-specific runtime placement

`PlatformDeployment` owns concrete topography overlays. `RepoGraph` may define
shared topography concepts, but it does not own deployment execution.

## Practical rule

- if you are naming things, you are probably in ontology
- if you are wiring things together, you are probably in topology
- if you are describing where things live, you are probably in topography

## Related

- [Architecture Charter](../architecture/platform-architecture-charter.md)
- [Ecosystem Overview](../overview/ecosystem.md)
- [Repository Catalog](../repos/index.md)
