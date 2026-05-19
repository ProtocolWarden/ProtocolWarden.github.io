# Ecosystem Graph

```mermaid
graph TD
    FRONT[ProtocolWarden/ProtocolWarden]
    OC[OperatorConsole]
    OPS[OperationsCenter]
    SB[SwitchBoard]
    CX[CxRP]
    RX[RxP]
    CR[CoreRunner\nsubprocess safety layer]
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
    OPS -->|direct_local / aider_local| CR
    OPS --> TE
    OPS --> DE
    OPS --> CE
    OPS --> PM
    OPS --> PT
    OPS --> SR
    OPS --> CU
    TE -->|safe_run| CR
    DE -->|safe_run| CR
    CE -->|safe_run| CR
    TE --> CX
    TE --> RX
    DE --> CX
    DE --> RX
    CE --> CX
    CE --> RX
    WS --> OPS
    WH --> OPS
```

CoreRunner is the canonical subprocess safety library for all backends.
OC's `direct_local` and `aider_local` use `CoreRunner.run()` (full RxP path).
TeamExecutor, DAGExecutor, and CritiqueExecutor use `core_runner.safe_run()` (lightweight primitive).
