# Architectural Invariants

Core invariants that every platform component must uphold:

- protocol repos own canonical protocol semantics
- manifest repos own topology and visibility truth
- public outputs are safe projections, not independent drift copies
- unknown visibility fails closed
- orchestrators consume, but do not absorb, protocol or topology ownership
- graph-language libraries own vocabulary, not graph instances or deployment truth

## Per-repo invariants

| Repo | Must always be | Must never become |
|------|---------------|-------------------|
| RepoGraph | graph-semantics library (ontology, topology, projection vocabulary) | graph instance owner, private truth holder, orchestrator |
| PlatformManifest | public graph instance + projection publisher | semantic vocabulary owner, private data store, orchestrator |
| PlatformDeployment | local topography and runtime placement truth | canonical architecture owner, ontology owner |
| Warehouse | context packaging utility | platform authority, topology owner, scheduler |
| PrivateManifest | private graph overlay (names, restricted edges) | public projection authority, canonical semantic owner |
| Custodian | audit engine and drift detector | topology truth holder, orchestration behavior owner |
| OperationsCenter | orchestration and task dispatch | canonical ontology owner, private manifest holder |

## Machine-checked invariants (ARCH detectors)

The following are enforced on every `custodian audit` run:

| Detector | Scope | Checks |
|----------|-------|--------|
| ARCH1 | Warehouse | README describes it as a context packaging utility, not a platform or governance authority |
| ARCH2 | PrivateManifest | Does not define its own manifest vocabulary (schema files, Enum/RelationshipKind/ProjectionBehavior in Python) |
| ARCH3 | PlatformDeployment | Docs do not claim canonical architecture ownership |
| ARCH4 | RepoGraph | README does not claim graph instance ownership, private truth, or orchestration behavior |

## Cross-repo import enforcement (X2)

X2 checks that every cross-repo Python import has a declared edge in
`PlatformManifest`. Undeclared imports fail the audit. The manifest is the
machine-readable source of truth for which repos depend on which.
