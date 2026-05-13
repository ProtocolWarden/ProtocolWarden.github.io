# Repository Catalog

This catalog explains what each major repo does and, more importantly, what it
does not do.

## Canonical repos

| Repo | Role | Notes |
| --- | --- | --- |
| [OperationsCenter](operationscenter.md) | orchestration consumer | consumes composed graph truth, does not own graph semantics |
| [OperatorConsole](operatorconsole.md) | operator-facing control surface | local operator workflows and observability, not graph semantics |
| [PlatformManifest](platformmanifest.md) | public graph publisher | public-safe projection surface backed by RepoGraph |
| [Custodian](custodian.md) | boundary verifier | fail-closed drift and boundary enforcement |
| [CxRP](cxrp.md) | cross-repo protocol | contract surface for execution and routing |
| [RxP](rxp.md) | runtime protocol | runtime invocation semantics |
| [ExecutorRuntime](executorruntime.md) | runtime mechanics | execution mechanics and adapters |
| [SwitchBoard](switchboard.md) | lane selection | routing and backend selection |
| [SourceRegistry](sourceregistry.md) | source inventory | source and capability registry |
| [PlatformDeployment](platformdeployment.md) | deployment/topography overlay | runtime glue and local/CI ergonomics |
| [Warehouse](warehouse.md) | context packaging utility | packaging and staging only |

## Managed projects

The public site does not catalog private-truth repos as normal browsable repo
pages. Managed projects are described at the ecosystem level instead of being
listed as first-class catalog entries here.

The public repo catalog is curated by the governance policy described in
[Public Repository Catalog](../governance/public-repo-catalog.md).

## Related pages

- [Overview](../overview/index.md)
- [Architecture Charter](../architecture/platform-architecture-charter.md)
- [Ontology](../ontology/index.md)
- [Topology](../topology/ecosystem-graph.md)
