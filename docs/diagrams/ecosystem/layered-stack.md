# Ecosystem Layered Stack

```mermaid
graph TD
    subgraph surface ["Public Surface"]
        DOCS["ProtocolWarden.github.io"]
        README["ProtocolWarden/ProtocolWarden"]
    end
    subgraph semantic ["Semantic / Protocol Layer"]
        RG[RepoGraph]
        PM[PlatformManifest]
        CX[CxRP]
        RX[RxP]
    end
    subgraph control ["Control / Runtime Layer"]
        OPS[OperationsCenter]
        SB[SwitchBoard]
        OC[OperatorConsole]
        ER[ExecutorRuntime]
    end
    subgraph gov ["Governance / Lifecycle Layer"]
        CU[Custodian]
        SR[SourceRegistry]
        PD[PlatformDeployment]
        WH[Warehouse]
    end

    surface --> semantic
    semantic --> control
    control --> gov
```

## Layer descriptions

| Layer | Purpose |
| --- | --- |
| Public Surface | Public-facing knowledge and orientation surfaces |
| Semantic / Protocol Layer | Graph language, public projection, execution and runtime contracts |
| Control / Runtime Layer | Orchestration, routing, operator entry, runtime invocation |
| Governance / Lifecycle Layer | Audit, source tracking, deployment, context packaging |
