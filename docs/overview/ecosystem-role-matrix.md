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
| Runtime Execution Layer | invocation mechanics and adapters | `ExecutorRuntime`, `VideoFoundry` |
| Governance / Audit Layer | boundary, drift, and catalog enforcement | `Custodian` |
| Deployment / Local Runtime Layer | environment assembly and convenience wrappers | `PlatformDeployment` |
| Source Lifecycle Layer | source and fork inventory | `SourceRegistry` |
| Context Staging Layer | LLM-ready packaging and staging | `Warehouse` |
| External Backend Layer | adapter candidates and forked dependencies | `Archon`, `firecrawl`, `kodo`, `PraisonAI`, `Wan2GP`, `openclaw`, `Zonos-API`, `neuro-game-sdk` |

## Boundary reminder

- `PrivateManifest` is private-truth documentation and boundary source, not a
  browseable public catalog entry.
- The public site explains it where the boundary needs to be understood.

