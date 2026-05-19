# Ecosystem Graph

```mermaid
graph TD
    FRONT[ProtocolWarden/ProtocolWarden]
    OC[OperatorConsole]
    OPS[OperationsCenter]
    SB[SwitchBoard]
    CX[CxRP]
    RX[RxP]
    ER[ExecutorRuntime\nsubprocess substrate]
    TE[TeamExecutor]
    DE[DAGExecutor]
    CE[CritiqueExecutor]
    RG[RepoGraph]
    PM[PlatformManifest]
    PT[Private truth layer]
    CU[Custodian]
    WS[PlatformDeployment]
    WH[Warehouse]
    SR[SourceRegistry]
    DOCS[ProtocolWarden.github.io]

    FRONT --> DOCS
    DOCS --> PM
    DOCS --> RG
    DOCS --> CX
    DOCS --> RX
    OC --> OPS
    OPS --> SB
    OPS --> CX
    OPS --> RX
    OPS -->|direct_local / aider_local adapters| ER
    OPS --> TE
    OPS --> DE
    OPS --> CE
    OPS --> PM
    OPS --> PT
    OPS --> SR
    OPS --> CU
    TE --> CX
    TE --> RX
    DE --> CX
    DE --> RX
    CE --> CX
    CE --> RX
    WS --> OPS
    WH --> OPS
```

ExecutorRuntime is a subprocess mechanics library — not a peer AI execution backend.
It is used by OC's `direct_local` and `aider_local` adapters only.
TeamExecutor, DAGExecutor, and CritiqueExecutor do not use it.
