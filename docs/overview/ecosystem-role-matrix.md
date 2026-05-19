# Ecosystem Role Matrix

This matrix is the fast answer to “what owns what?” for the public ecosystem.

| Layer | Purpose | Main repos |
| --- | --- | --- |
| Profile Front Door | short public orientation | `ProtocolWarden/ProtocolWarden` |
| Public Knowledge Surface | canonical documentation and public projection | `ProtocolWarden.github.io` |
| Semantic Graph Layer | shared graph language and schema governance | `RepoGraph`, `PlatformManifest` |
| Contract Protocol Layer | execution and runtime contracts | `CxRP`, `RxP` |
| Control Plane Layer | planning and orchestration consumer | `OperationsCenter` |
| Routing Policy Layer | lane and backend selection | `SwitchBoard` |
| Operator Entry Layer | operator workspace and command surface | `OperatorConsole` |
| Runtime Execution Layer | invocation mechanics and adapters | `ExecutorRuntime`, backend consumers |
| Governance / Audit Layer | boundary, drift, and catalog enforcement | `Custodian` |
| Deployment / Local Runtime Layer | environment assembly and convenience wrappers | `PlatformDeployment` |
| Source Lifecycle Layer | source and fork inventory | `SourceRegistry` |
| Context Staging Layer | LLM-ready packaging and staging | `Warehouse` |
| Execution Backend Layer | owned AI task executors | `TeamExecutor`, `DagExecutor`, `CritiqueExecutor` |
| External Layer | forked dependencies and third-party integrations | `firecrawl`, `openclaw`, `PraisonAI`, `Wan2GP`, `Zonos-API`, `neuro-game-sdk` |

> **ADR 0005 (2026-05-18):** `kodo` (→ TeamExecutor) and `Archon` (→ DagExecutor) retired as external forks. See [TeamExecutor](../repos/teamexecutor.md), [DagExecutor](../repos/dagexecutor.md), [CritiqueExecutor](../repos/critiqueexecutor.md).

## Boundary reminder

- private-truth repositories are documentation and boundary sources, not
  browseable public catalog entries.
- The public site explains it where the boundary needs to be understood.
