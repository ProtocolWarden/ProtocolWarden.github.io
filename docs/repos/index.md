# Repository Catalog

This catalog explains what each major repo does and, more importantly, what it
does not do.

## Core platform repos

| Repo | Category | Role |
| --- | --- | --- |
| [RepoGraph](repograph.md) | semantic_core | shared graph language, schema governance, projection semantics, boundary artifact semantics |
| [PlatformManifest](platformmanifest.md) | topology_projection | public-safe graph publisher and projection surface |
| [CxRP](cxrp.md) | contract_protocol | contract execution routing semantics |
| [RxP](rxp.md) | contract_protocol | runtime execution semantics |
| [OperationsCenter](operationscenter.md) | control_plane | orchestration consumer and execution coordinator |
| [SwitchBoard](switchboard.md) | routing_policy | lane and backend selection |
| [OperatorConsole](operatorconsole.md) | operator_entrypoint | operator-facing control surface |
| [ExecutorRuntime](executorruntime.md) | runtime_execution | runtime invocation mechanics and adapters |
| [Custodian](custodian.md) | governance_audit | boundary, drift, and semantic federation verifier |
| [PlatformDeployment](platformdeployment.md) | deployment_runtime | runtime glue and local/CI ergonomics |
| [SourceRegistry](sourceregistry.md) | source_lifecycle | source and fork inventory |
| [Warehouse](warehouse.md) | context_staging | LLM-ready packaging and staging |
| [VideoFoundry](videofoundry.md) | backend_candidate | runtime and content-pipeline consumer surface |

## Adjacent surfaces

| Repo | Category | Notes |
| --- | --- | --- |
| [External Integrations](external-integrations.md) | integration_surface | forks, adapters, and backend candidates documented separately |

## Boundary note

`PrivateManifest` is intentionally not a browseable repo page in the public
catalog. The architecture charter and boundary workflow docs name it where the
private-truth boundary must be explained.

## Related pages

- [Overview](../overview/index.md)
- [Architecture Charter](../architecture/platform-architecture-charter.md)
- [Ontology](../ontology/index.md)
- [Topology](../topology/ecosystem-graph.md)
- [Public Repository Catalog Policy](../governance/public-repo-catalog.md)
