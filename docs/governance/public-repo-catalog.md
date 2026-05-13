# Public Repository Catalog

This page defines the public-surface catalog policy for the browseable repo
index. It is a curation rule, not a privacy detector. Privacy detectors still
own leakage and boundary enforcement.

The browseable repository catalog on this site is curated. It lists approved
public repo pages and does not turn private-truth repos into first-class public
catalog entries.

## Policy

- Architecture and charter pages may name `PrivateManifest` when they describe
  the private-truth boundary.
- The public repo catalog itself is limited to approved public pages.
- This policy does not replace privacy detectors; it complements them.
- The public site exposes current pages only.
- External integrations and backend candidates are documented separately from
  the core repo catalog.

## Approved catalog pages

| Repo | Category | Purpose | Public role | Not responsible for | Primary consumers | License | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| RepoGraph | semantic_core | shared graph semantics and boundary schema | canonical graph language | private truth, orchestration, deployment, UI projection | PlatformManifest, Custodian, OperationsCenter | repo license | active |
| PlatformManifest | topology_projection | public graph projection publisher | public-safe repo graph surface | private truth, orchestration policy, deployment control | docs site, OperationsCenter | repo license | active |
| CxRP | contract_protocol | execution routing contract models | contract vocabulary for routing | runtime hosting, orchestration policy | OperationsCenter, SwitchBoard, ExecutorRuntime | repo license | active |
| RxP | contract_protocol | runtime invocation contract models | normalized runtime invocation vocabulary | runtime hosting, orchestration policy | ExecutorRuntime, OperationsCenter | repo license | active |
| OperationsCenter | control_plane | planning and orchestration consumer | control-plane coordinator | graph semantics, projection semantics | SwitchBoard, ExecutorRuntime, Custodian | repo license | active |
| SwitchBoard | routing_policy | lane selection policy | backend and lane selector | graph semantics, runtime execution | OperationsCenter | repo license | active |
| OperatorConsole | operator_entrypoint | operator-facing entrypoint | local operator workspace | graph semantics, runtime hosting | OperationsCenter, Custodian | repo license | active |
| ExecutorRuntime | runtime_execution | runtime mechanics | contract consumer and executor | graph semantics, orchestration policy | OperationsCenter | repo license | active |
| Custodian | governance_audit | boundary and drift verifier | fail-closed verifier | graph semantics, orchestration, deployment | all public repos | repo license | active |
| PlatformDeployment | deployment_runtime | local/CI runtime glue | environment assembly and wrapper layer | graph semantics, orchestration policy | Custodian, OperationsCenter | repo license | active |
| SourceRegistry | source_lifecycle | source and fork tracking | source inventory and lifecycle | graph semantics, orchestration policy | OperationsCenter, Custodian | repo license | active |
| Warehouse | context_staging | LLM-ready context packaging | utility-only packaging/staging | graph authority, orchestration, governance | operators, assistant workflows | repo license | active |
| VideoFoundry | backend_candidate | content pipeline consumer | adjacent runtime/backend surface | graph semantics, orchestration authority | docs site, OperationsCenter | repo license | active |

## Related pages

- [Overview](../overview/index.md)
- [Architecture Charter](../architecture/platform-architecture-charter.md)
- [Ontology](../ontology/index.md)
- [Topology](../topology/ecosystem-graph.md)
- [Profile README vs Pages Site](profile-readme-vs-pages-site.md)
- [External Integrations](external-integrations.md)
